# Ansible Ad-Hoc Commands

Ad-hoc commands in Ansible are simple, one-liner commands used to perform quick tasks on managed nodes without the need for a full playbook. They are useful for testing connectivity, gathering facts, or making quick configuration changes.

---

## Basic Syntax

The general syntax for an ad-hoc command is:

```bash
ansible <host-pattern> -m <module-name> -a "<module-arguments>"
```

*   `<host-pattern>`: Specifies which hosts from your inventory to target (e.g., `all`, `webservers`, `192.168.1.10`).
*   `-m <module-name>`: Specifies the Ansible module to use (e.g., `ping`, `command`, `shell`, `copy`).
*   `-a "<module-arguments>"`: Provides arguments to the module.

---

## Common Ad-Hoc Command Examples

### 1. Ping all hosts

This command uses the `ping` module to test connectivity to all hosts defined in your inventory.

```bash
ansible all -m ping
```

### 2. Check system uptime

This command uses the `command` module to execute the `uptime` command on all hosts.

```bash
ansible all -a "uptime"
```

### 3. Run commands as root (become)

The `-b` (or `--become`) flag allows you to run commands with elevated privileges (e.g., `sudo`).

```bash
ansible all -b -a "whoami"
```

### 4. Copy content to a file (using `copy` module)

The `copy` module is used to copy files from the control node to managed nodes, or to create files with specific content.

*   **`--check`**: Performs a "dry run" to show what changes *would* be made without actually making them.
*   **`--diff`**: Shows the differences between the current state and the desired state.

```bash
# Perform a dry run to see what would happen
ansible all -b -m copy -a "content='# This file was configured by ansible #' dest=/etc/motd" --check

# Show the differences without applying changes
ansible all -b -m copy -a "content='# This file was configured by ansible #' dest=/etc/motd" --diff

# Perform a dry run and show differences
ansible all -b -m copy -a "content='# This file was configured by ansible #' dest=/etc/motd" --check --diff
```

### 5. Using `shell` module for commands with pipes or redirection

The `shell` module allows you to run commands that require shell features like pipes (`|`), redirection (`>`), or environment variables.

```bash
ansible all -m shell -a "echo 'Hello from Ansible' > /tmp/ansible_message.txt"
```

### 6. Using `raw` module for devices without Python

The `raw` module is used to execute commands directly on remote hosts, bypassing Ansible's Python-based module system. This is useful for bootstrapping Python on new hosts or managing devices that do not have Python installed (e.g., some network devices).

```bash
ansible all -m raw -a "ls -l /"
```

---

## Viewing Module Documentation

To get detailed information about any Ansible module, use the `ansible-doc` command:

```bash
ansible-doc <module_name>
```

Example:

```bash
ansible-doc copy
```

Press `q` to exit the documentation viewer.

---

## Summary

Ad-hoc commands are a quick and efficient way to interact with your managed nodes for simple tasks. For more complex, repeatable, and structured automation, playbooks are the preferred method.
