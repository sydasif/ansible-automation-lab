# Ansible Installation on Vagrant-Managed Ubuntu

This guide focuses on installing Ansible on an Ubuntu virtual machine managed by Vagrant, which will serve as your Ansible control node within the lab environment.

---

## Prerequisites

Before proceeding, ensure you have:

*   A Vagrant-managed Ubuntu VM running (e.g., `ubuntu-64` from `lab-1/Vagrantfile`).
*   SSH access to your Vagrant VM with passwordless sudo configured, as described in the [Ansible Vagrant Lab Setup](ansible-vagrant-lab.md) guide.

---

## Installing Ansible on the Ubuntu Control Node

You can install Ansible on your Ubuntu VM using either `apt` (package manager) or `pip` (Python package installer). `pip` is generally recommended for getting the latest version of Ansible.

### Method 1: Install Ansible using `apt`

This method installs Ansible from the Ubuntu repositories.

1.  **Update package lists:**
    ```bash
    sudo apt update
    ```

2.  **Install software-properties-common (if not already installed):**
    ```bash
    sudo apt install software-properties-common -y
    ```

3.  **Add the Ansible PPA (Personal Package Archive):**
    This ensures you get a more recent version of Ansible than what might be in the default repositories.
    ```bash
    sudo apt-add-repository ppa:ansible/ansible -y
    ```

4.  **Install Ansible:**
    ```bash
    sudo apt install ansible -y
    ```

### Method 2: Install Ansible using `pip` (Recommended)

This method installs Ansible using Python's package installer, which often provides the latest version.

1.  **Update package lists and install Python 3 and pip:**
    ```bash
    sudo apt update
    sudo apt install python3 python3-pip git -y
    ```

2.  **Install Ansible using pip:**
    ```bash
    pip3 install ansible
    ```

---

## Verifying Ansible Installation

After installation, verify that Ansible is correctly installed and accessible.

1.  **Check Ansible version:**
    ```bash
    ansible --version
    ```

2.  **Test Ansible connectivity to localhost:**
    This command uses the `ping` module to ensure Ansible can run basic tasks.
    ```bash
    ansible localhost -m ping
    ```
    Expected output:
    ```plaintext
    localhost | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }
    ```

---

## Configuring Ansible Inventory

Ansible uses an inventory file to define the managed nodes it will interact with. For your Vagrant lab, you'll typically create a custom inventory.

1.  **Create an inventory file:**
    You can create a `hosts` file in your current working directory or specify its path when running Ansible commands. For example, create a file named `hosts` in the same directory as your playbooks:
    ```bash
    nano hosts
    ```

2.  **Add your Vagrant VMs to the inventory:**
    Based on `ansible-server/vagrant/lab-1/Vagrantfile`, your inventory might look like this:

    ```ini
    [fedora]
    centos-7 ansible_host=192.168.200.10 ansible_user=vagrant

    [ubuntu]
    ubuntu-64 ansible_host=192.168.200.11 ansible_user=vagrant

    [linux:children]
    fedora
    ubuntu
    ```
    *   `ansible_host`: Specifies the IP address of the managed node.
    *   `ansible_user`: Specifies the SSH user to connect with (for Vagrant, this is typically `vagrant`).

3.  **Test connectivity to your managed nodes:**
    From your Ansible control node (the Ubuntu VM), run a ping command targeting your managed nodes:
    ```bash
    ansible all -m ping -i hosts
    ```
    Expected output (similar to this for each host):
    ```plaintext
    centos-7 | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }
    ubuntu-64 | SUCCESS => {
        "changed": false,
        "ping": "pong"
    }
    ```

---

## Next Steps

You have successfully set up your Ansible control node within a Vagrant VM and configured your inventory. You are now ready to explore [Ansible Playbooks](ansible-server/03-playbook.md) and [Ad-Hoc Commands](ansible-server/ad-hoc-commands.md) to automate tasks on your managed nodes.
