# Ansible for Network Automation Overview

Automation is now a core part of network management, and Ansible offers a simple yet powerful way to achieve it. Designed first for servers and later extended to network devices, Ansible relies on concepts like modules and playbooks that work across both areas with slight adjustments for device-specific tasks. This unified approach helps network engineers manage servers and network equipment in the same framework, reducing manual effort and improving operational efficiency without requiring deep programming knowledge.

### Push vs Pull Model

In automation, a push model is when a central server delivers commands or configurations directly to managed nodes, which is how Ansible works, while a pull model is when nodes regularly contact a central server to retrieve and apply updates, a method used by tools like Puppet, Chef, and SaltStack.

### Ansible's Approach to Automation

Ansible provides a practical way to automate networks, valued for its simplicity and suitability for engineers without programming experience.

It runs tasks in order through playbooks while also supporting device-friendly methods like NETCONF and RESTCONF for broader flexibility.

Engineers only need to learn YAML, which makes writing playbooks straightforward and easy to follow. Compared to traditional Python scripts, Ansible offers built-in concurrency, enabling tasks to run across many nodes at once, reducing deployment time and ensuring consistent results.

---

## Getting Started with Ansible for Network Automation

Ansible makes network automation easier by supporting a wide range of vendors and device types. It helps engineers automate routine tasks while keeping configurations consistent across the entire network.

### Communication Methods

* **network_cli (SSH):** Secure and common for device management.
* **netconf (SSH):** Built for network configuration and monitoring.
* **httpapi (HTTP/HTTPS):** Useful for devices with RESTful APIs.

### Supported Platforms

* **Arista EOS**
* **Cisco IOS, IOS-XR, NX-OS**
* **Juniper Junos**
* **VyOS**

Ansible’s broad protocol and platform support simplifies network management and improves efficiency.

### Network Modules in Ansible

Unlike regular Ansible modules, network modules do not run on the managed devices because most network gear cannot execute Python. Instead, these modules run on the Ansible control node, which also serves as the location for backup files, usually saved in the backup directory under the playbook root.

This setup lets Ansible manage network devices consistently while providing backup capabilities without requiring Python on the devices.

### Privilege Escalation - Networking Device

Starting with Ansible 2.6, you can use the parameter become: yes with become_method: enable to run tasks, plays, or playbooks with elevated privileges on network platforms that support privilege escalation.

### Establish a Manual Connection to a Managed Node

Before running  any Anisble playbook, verify your access, connect to the network device directly and pull its configuration. Replace the placeholder username and device name with your own credentials. For example, to log in to a router at 172.16.10.11 from the [Lab Setup](https://github.com/sydasif/gns3-lab) using SSH to avoid SSH error in run time.

```bash
zolo@u22s:~$ ssh admin@172.16.10.11
(admin@172.16.10.11) Password:

r1#sh ip int bri
Interface                  IP-Address      OK? Method Status                Protocol
FastEthernet0/0            172.16.10.11    YES NVRAM  up                    up
FastEthernet0/1            unassigned      YES NVRAM  administratively down down
FastEthernet1/0            unassigned      YES unset  administratively down down
r1#exit
Connection to 172.16.10.11 closed.
```

### Run Your First Network Command (Ad-Hoc)

Instead of manually connecting and running a command on the network device, you can retrieve its configuration with a single, stripped-down Ansible command. For more details on ad-hoc commands, refer to the [Ad-Hoc Commands](./ansible-ad-hoc.md) guide.

```terminal
zolo@u22s:~$ ansible all -i 172.16.10.12, -c network_cli -u admin -k -m ios_facts -e ansible_network_os=ios
SSH password:
172.16.10.12 | SUCCESS => {
    "ansible_facts": {
        "ansible_net_api": "cliconf",
        "ansible_net_gather_network_resources": [],
        "ansible_net_gather_subset": [
            "default"
        ],
        "ansible_net_hostname": "core-sw",
        "ansible_net_image": "tftp://255.255.255.255/unknown",
        "ansible_net_iostype": "IOS",
        "ansible_net_model": "3725",
        "ansible_net_operatingmode": "autonomous",
        "ansible_net_python_version": "3.10.12",
        "ansible_net_serialnum": "FTX0945W0MY",
        "ansible_net_system": "ios",
        "ansible_net_version": "12.4(15)T14",
        "ansible_network_resources": {}
    },
    "changed": false
}
```

In this example, Ansible targets all hosts defined in the inventory, specifying a custom inventory file with `-i`, connecting using `network_cli` as the connection type with `-c`, authenticating with the username `admin` using `-u`, prompting for a password with `-k`, executing the `ios_facts` module to gather facts about IOS devices, and specifying the network platform as `ios` using `-e`.

### Key Parameters for Network Ad-Hoc Commands

*   `-i`: Specifies the list of managed nodes, separated by commas, or the path to an inventory file.
*   `-c`: Defines the connection type (e.g., `network_cli`, `netconf`).
*   `-u`: Specifies the username for authentication.
*   `-k`: Prompts for a password.
*   `-m`: Specifies the module name (e.g., `ios_facts`, `ios_command`).
*   `-e`: Defines additional variables, such as the network platform (`ansible_network_os`).

These ad-hoc commands provide quick and efficient ways to perform specific tasks across your network infrastructure using Ansible's versatile command-line interface.

## Test Your Ansible - Playbook

Ansible playbooks are at the heart of automation. They describe what you want to do in simple YAML, and each play is made up of tasks that Ansible runs step by step. To see this in action, let’s start with a very basic playbook that gathers information from IOS devices and then displays it back.

```yaml
---
- name: "Playbook-1: Get ios facts"
  hosts: all
  gather_facts: false
  connection: network_cli

  tasks:
    - name: "P1T1: Get config from ios_facts"
      ios_facts:
        gather_subset: all

    - name: "P1T2: Display debug message"
      debug:
        msg: "The {{ ansible_net_hostname }} has {{ ansible_net_iostype }} platform"
```

Here’s what’s happening: we’ve given the play a name for clarity, pointed it at all hosts in the inventory, and told Ansible to skip its default fact-gathering since we’ll use `ios_facts` instead. The first task collects details from the IOS devices, and the second task prints a simple debug message showing the device’s hostname and platform type.

To run the playbook, just use:

```bash
ansible-playbook playbook.yml
```

When you execute it, you’ll see Ansible connect to each device, gather the facts, and then display messages like:

```bash
zolo@u22s:~/ansible-networking-lab$ ansible-playbook 01_play.yaml

PLAY [Playbook-1: Get ios facts] ********************************************************************************************************************

TASK [P1T1: Get config from ios_facts] **************************************************************************************************************
ok: [access1]
ok: [access2]
ok: [r1]
ok: [core-sw]

TASK [P1T2: Display debug message] ******************************************************************************************************************
ok: [r1] => {
    "msg": "The r1 has IOS platform"
}
ok: [access1] => {
    "msg": "The access1 has IOS platform"
}
ok: [core-sw] => {
    "msg": "The core-sw has IOS platform"
}
ok: [access2] => {
    "msg": "The access2 has IOS platform"
}
```

This might look simple, but it demonstrates how easily you can start managing devices with Ansible. From here, you can build on this foundation to add more tasks, manage larger groups of devices, or roll out more complex changes.
