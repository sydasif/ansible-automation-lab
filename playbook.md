# Playbook in Ansible

Ansible Playbooks are YAML files used to define the automation tasks to be executed on managed nodes. Playbooks simplify configuration management, enabling organized, readable, and reusable automation workflows.

---

## Basic Example

```yaml
---
- name: Basic Playbook
  hosts: all
  tasks:
    - name: Save system information
      shell: uname -a > /home/zolo/sysinfo.txt

    - name: Save current user information
      shell: whoami >> /home/zolo/sysinfo.txt
```

Run this playbook using the command:

```bash
ansible-playbook playbooks/basic_playbook.yml
```

**Output Example:**

```plaintext
PLAY [Basic Playbook] ********************************************************************

TASK [Gathering Facts] *****************************************************************
ok: [rhel-9]

TASK [Save system information] ********************************************************
changed: [rhel-9]

TASK [Save current user information] **************************************************
changed: [rhel-9]

PLAY RECAP *****************************************************************************
rhel-9 : ok=3  changed=2  unreachable=0  failed=0  skipped=0  rescued=0  ignored=0
```

**Explanation:**

- The playbook targets the `linux` group of hosts.
- It executes two tasks: capturing system and user information, saving them to a file on the target machine.

---

### Removing Files Example

```yaml
---
- name: Remove File Example
  hosts: linux
  tasks:
    - name: Delete a file
      file:
        path: /home/vagrant/sysinfo.txt
        state: absent
```

Run this playbook:

```bash
ansible-playbook playbooks/remove_file.yml
```

**Output Example:**

```plaintext
TASK [Delete a file] *******************************************************************
changed: [linux-host]
```

---

### Using Variables in Playbooks

Variables make playbooks flexible. Here's an example:

```yaml
---
- name: Using Variables
  hosts: linux
  vars:
    my_var: Hello World
  tasks:
    - name: Print variable to terminal
      command: echo "{{ my_var }}"
      register: result

    - name: Show command output
      debug:
        msg: "{{ result.stdout_lines }}"
```

Run this playbook and see:

```plaintext
TASK [Show command output] *************************************************************
ok: [linux-host] => {
    "msg": [
        "Hello World"
    ]
}
```

---

### Playbook with Multiple Plays

A playbook can include multiple plays to manage different host groups or tasks:

```yaml
---
- name: Install on Ubuntu
  hosts: ubuntu
  become: true
  tasks:
    - name: Install Git
      apt:
        name: git
        state: present

- name: Install on CentOS
  hosts: centos
  become: true
  tasks:
    - name: Install Git
      yum:
        name: git
        state: present
```

**Output Example:**

```plaintext
PLAY [Install on Ubuntu] ***************************************************************
TASK [Install Git] *********************************************************************
ok: [ubuntu]

PLAY [Install on CentOS] ***************************************************************
TASK [Install Git] *********************************************************************
ok: [centos]
```

---

### Conditional Task Execution (`when` Statement)

Use the `when` statement to conditionally execute tasks:

```yaml
---
- name: Conditional Installation
  hosts: linux
  become: true
  tasks:
    - name: Install Git on Ubuntu
      apt:
        name: git
        state: latest
      when: ansible_distribution == "Ubuntu"

    - name: Install Git on CentOS
      yum:
        name: git
        state: latest
      when: ansible_distribution == "CentOS"
```

**Ad-Hoc Command to Check Host Distribution:**

```bash
ansible all -m gather_facts --limit centos | grep ansible_distribution
```

**Sample Output:**

```plaintext
"ansible_distribution": "CentOS",
```

**Output of Playbook:**

```plaintext
TASK [Install Git on Ubuntu] **********************************************************
skipping: [centos]
changed: [ubuntu]

TASK [Install Git on CentOS] **********************************************************
skipping: [ubuntu]
changed: [centos]
```

---

### Summary

Ansible Playbooks are:

- Written in YAML for clarity and simplicity.
- Organized into plays targeting specific host groups.
- Capable of handling variables, conditions, and multiple plays for flexibility.

This structure helps automate tasks across various environments efficiently!
