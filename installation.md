# Ansible Installation on Ubuntu

This guide focuses on installing Ansible on an Ubuntu virtual machine, which will serve as your Ansible control node within the lab environment.

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
If you see a "pong" response, Ansible is successfully installed and functioning on your control node.
