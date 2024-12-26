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

1. Install **QEMU/KVM** on your host machine (e.g., RHEL 9).
2. Create virtual machines:
   - Fedora 39
   - Ubuntu 22

---

## Setting Up the Lab

1. **Edit the `/etc/hosts` file** to map IPs to hostnames:

```bash
sudo nano /etc/hosts
```

Add:

```text
192.168.122.10  f39s
192.168.122.11  u22s
```

2. **Set up SSH keys** for passwordless login:

```bash
ssh-keygen
ssh-copy-id -i .ssh/id_rsa.pub zolo@f39s
ssh-copy-id -i .ssh/id_rsa.pub zolo@u22s
```

3. **Allow passwordless sudo**:

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

Install Ansible on the control node using `pip`:

```bash
pip3 install ansible-core
```

Verify the installation:

```bash
ansible --version
```

---

## Configuring Managed Nodes

Create an inventory file to list managed nodes:

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

## Running Ad-Hoc Commands

Ad-hoc commands are simple, one-time tasks you can run without writing a playbook.

### Examples

1. **Ping all hosts**:

```bash
ansible -m ping all
```

2. **Check uptime**:

```bash
ansible all -a "uptime"
```

3. **Run commands as root**:

```bash
ansible all -b -a "whoami"
```

### Key Points

- Use `-m` to specify a module (e.g., `ping`, `command`).
- Add `-b` to run commands as root.

---

## Understanding Ansible Modules

Modules are like tools for specific tasks.

| **Module**   | **Purpose**                                      | **Example**                             |
|--------------|--------------------------------------------------|-----------------------------------------|
| `ping`       | Test if devices are reachable.                   | `ansible -m ping all`                   |
| `command`    | Run simple commands (no pipes or redirects).     | `ansible all -m command -a "uptime"`    |
| `shell`      | Run commands with pipes or redirection.          | `ansible all -m shell -a "echo hello"`  |
| `raw`        | Run commands on devices without Python.          | `ansible all -m raw -a "ls"`            |

---

## Viewing Module Documentation

To learn about a module, use:

```bash
ansible-doc <module_name>
```

Example:

```bash
ansible-doc ping
```

Press `q` to exit.

---

### Next Steps

Once you’re comfortable running ad-hoc commands, you can move on to writing playbooks to automate complex tasks. Ansible’s simplicity and versatility make it a great choice for beginners and advanced users alike!
