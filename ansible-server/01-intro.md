# Ansible Lab Setup with KVM

Ansible is a tool used for automating tasks like configuring servers, managing networks, or deploying applications. It’s agentless, meaning it doesn’t require installation on remote devices if Python and SSH are available. For network devices, Ansible may connect via APIs or other protocols.

---

## How Ansible Works

Ansible works in steps:

1. **Creates a script** for the task.
2. **Copies the script** to the remote device.
3. **Runs the script** on the remote device.
4. **Removes the script** after completion.

Key points:

- Tasks run in order across all devices.
- Ansible waits for all devices to complete one task before moving to the next.

---

## Why Use Ansible?

1. **Easy to understand** syntax.
2. No need to install anything on remote devices.
3. Uses **push-based architecture**—commands are sent from the control node.
4. Comes with built-in **modules** for different tasks.

---

## What You Need

### Control Node

- A system with Python 3.5 or higher (e.g., Fedora, Ubuntu, RHEL, etc.).

### Managed Nodes

- Devices accessible via SSH. Python should be installed unless the device is a network switch/router.

### Lab Setup

This lab focuses on setting up a control node and managed nodes using KVM. For a Vagrant-based lab setup, refer to the [Ansible Vagrant Lab Setup](ansible-server/vagrant/ansible-vagrant-lab.md) guide.

1. Install **QEMU/KVM** on your host machine (e.g., RHEL 9).
2. Create virtual machines:
   - Fedora 39
   - Ubuntu 22

---

## Setting Up the Lab

1. **Edit the `/etc/hosts` file** to map IPs to hostnames on your control node:

```bash
sudo nano /etc/hosts
```

Add:

```text
192.168.122.10  f39s
192.168.122.11  u22s
```

2. **Set up SSH keys** for passwordless login from your control node to managed nodes:

```bash
ssh-keygen
ssh-copy-id -i .ssh/id_rsa.pub zolo@f39s
ssh-copy-id -i .ssh/id_rsa.pub zolo@u22s
```

3. **Allow passwordless sudo** on your managed nodes:

- Log into each managed node.
- Edit the sudoers file:

```bash
sudo visudo
```

- Add:

```text
zolo ALL=(ALL) NOPASSWD: ALL
```

---

## Installing Ansible

For detailed instructions on installing Ansible, refer to the [Ansible Installation on Vagrant-Managed Ubuntu](ansible-server/vagrant/ansible-installation-on-vagrant.md) guide, which covers both `apt` and `pip` methods.

---

## Configuring Managed Nodes

Create an inventory file to list managed nodes. For more details on inventory, refer to the [Ansible Inventory Documentation](https://docs.ansible.com/ansible/2.9/user_guide/intro_inventory.html#how-to-build-your-inventory).

Example `hosts` file:

```bash
nano hosts
```

Add:

```text
[fedora]
f39s ansible_user=zolo

[ubuntu]
u22s ansible_user=zolo
```

---

## Next Steps

Once your lab is set up and Ansible is installed, you can proceed to learn about [Ad-Hoc Commands](ansible-server/ad-hoc-commands.md) and [Ansible Playbooks](ansible-server/03-playbook.md) to automate tasks.
