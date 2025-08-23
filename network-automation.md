# Ansible for Network Automation Overview

Automation in network management has become crucial in modern IT environments, and understanding the models and tools available is essential for network engineers. This introduction will guide you through the fundamentals of Ansible automation, emphasizing its practical advantages and ease of adoption, especially for those without extensive programming skills.

Ansible initially focused on managing servers but has since extended its capabilities to include network devices. The core concepts, including modules and playbooks, remain consistent between server and network management, though there are some differences tailored to network automation. This expansion allows for a unified approach to managing both servers and network equipment, streamlining IT operations and improving efficiency.

### What is a Push Model?

In automation, a push model refers to a system where the central server sends commands or configurations directly to managed nodes. Ansible operates on a push model, meaning it pushes configurations from a central control machine to the nodes it manages.

### What is a Pull Model?

Conversely, a pull model involves managed nodes periodically checking in with a central server to fetch and apply new configurations. This approach is often seen in tools like Puppet, Chef, and SaltStack.

### Ansible's Approach to Automation

Ansible is renowned for its simplicity and accessibility, particularly for network engineers who may not have a background in programming. Ansible operates in a procedural manner, where tasks are executed sequentially as defined in playbooks. This straightforward approach is enhanced by Ansible’s support for declarative models through technologies like NETCONF and RESTCONF, allowing for more flexible and scalable network management.

### Ease of Adoption for Network Engineers

For network engineers looking to automate tasks without diving into complex programming, Ansible is an excellent choice. The primary requirement is an understanding of YAML, the human-readable data serialization standard used to write Ansible playbooks. With YAML, network engineers can define tasks, configurations, and workflows in a clear and concise manner.

### Built-In Concurrency

One of Ansible's significant advantages over traditional Python scripting is its built-in concurrency. Ansible allows for parallel execution of tasks across multiple nodes, significantly speeding up deployment times and ensuring consistent configurations.

## Getting Started with Ansible for Network Automation

Ansible modules support a wide range of vendors, device types, and actions, so you can manage your entire network with a single automation tool. This versatility makes Ansible a powerful solution for network automation, allowing you to automate routine tasks and ensure consistency across your network infrastructure. Ansible handles communication between the control node and managed nodes through multiple protocols:

*   **network_cli by SSH:** A widely-used protocol for managing network devices, ensuring secure and reliable communication.
*   **netconf by SSH:** A protocol designed specifically for network management, offering enhanced capabilities for configuration and monitoring.
*   **httpapi by HTTP/HTTPS:** A flexible and efficient protocol for interacting with network devices that support RESTful APIs.

Network platforms supported by Ansible are:

*   **Arista: eos:** Providing robust automation capabilities for Arista's Extensible Operating System.
*   **Cisco: ios, iosxr, nxos:** Enabling comprehensive management of Cisco's diverse range of network operating systems, from traditional IOS to the advanced features of IOS-XR and NX-OS.
*   **Juniper: junos:** Facilitating powerful automation for Juniper's Junos OS, known for its flexibility and performance.
*   **VyOS: vyos:** Supporting automation for VyOS, an open-source network operating system, ideal for various networking tasks.

With Ansible's extensive support for different network platforms and protocols, you can streamline your network automation processes and achieve greater operational efficiency.

### Network Modules in Ansible

Unlike most Ansible modules, network modules do not run on the managed nodes due to the inability of most network devices to run Python. Instead, these modules are executed on the Ansible control node. This different methodology ensures that Ansible can still manage network devices effectively. Additionally, network modules use the control node as a destination for backup files, typically storing them in the backup directory under the playbook root directory. This approach allows Ansible to provide consistent network management and backup capabilities without the need for Python on the network devices themselves.

### Privilege Escalation - Networking Device

As of Ansible 2.6, you can use the top-level Ansible parameter `become: yes` with `become_method: enable` to run a task, play, or playbook with escalated privileges on any network platform that supports privilege escalation.

### Establish a Manual Connection to a Managed Node

To confirm your credentials, connect to a network device manually and retrieve its configuration. Replace the sample user and device name with your real credentials. For example, for a router:

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

Instead of manually connecting and running a command on the network device, you can retrieve its configuration with a single, stripped-down Ansible command. For more details on ad-hoc commands, refer to the [Ansible Ad-Hoc Commands](ansible-server/ad-hoc-commands.md) guide.

```bash
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
