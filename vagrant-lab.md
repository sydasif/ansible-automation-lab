# Ansible Vagrant Lab Setup

This section guides you through setting up a virtual lab environment using Vagrant and VirtualBox (or VMware) to practice Ansible automation. Vagrant simplifies the process of creating and managing virtual machines, providing a consistent and reproducible environment for your labs.

---

## Requirements for this Lab

To follow this lab, you will need:

1.  **Virtualization Software:**
    *   [VirtualBox](https://www.virtualbox.org/wiki/Downloads) (recommended and free) or VMware Workstation/Fusion.
2.  **Vagrant:**
    *   [Download and install Vagrant](https://www.vagrantup.com/downloads) on your control node (your local machine). Refer to the [Vagrant Quick Start Guide](https://learn.hashicorp.com/tutorials/vagrant/getting-started-index?in=vagrant/getting-started) for detailed installation instructions.

---

## Setting Up Your Vagrant Environment

1.  **Create a Lab Directory:**
    Create a new directory on your local machine where you will store your Vagrant lab files. For example:
    ```bash
    mkdir ~/Documents/ansible-automation-lab/ansible-server/vagrant-lab
    cd ~/Documents/ansible-automation-lab/ansible-server/vagrant-lab
    ```

2.  **Choose a Vagrantfile:**
    You can use one of the provided `Vagrantfile` examples from this repository, or create your own.
    *   `server-lab/vagrant/lab-1/Vagrantfile`: Sets up a CentOS 7 and an Ubuntu Bionic 64 VM.
    *   `server-lab/vagrant/lab-2/Vagrantfile`: Sets up three Ubuntu 18.04 VMs (node01, node02, node03).

    For this example, let's use the `lab-1` Vagrantfile. Copy it into your `vagrant-lab` directory:
    ```bash
    cp ../lab-1/Vagrantfile .
    ```

3.  **Boot the Vagrant Devices:**
    Navigate to your `vagrant-lab` directory in your terminal and run:
    ```bash
    vagrant up
    ```
    This command will download the specified box images (if not already present), create, and boot the virtual machines. This process may take some time depending on your internet connection and system resources.

4.  **Check Device Status:**
    After booting, you can verify the status of your virtual machines:
    ```bash
    vagrant status
    ```

5.  **SSH into a Device:**
    You can SSH into any of your Vagrant-managed VMs using the `vagrant ssh` command followed by the VM's name (as defined in the `Vagrantfile`). For example:
    ```bash
    vagrant ssh ubuntu-64
    ```
    If you encounter SSH connection errors, refer to common troubleshooting guides like [SSH Permission Denied on StackOverflow](https://stackoverflow.com/questions/36300446/ssh-permission-denied-publickey-gssapi-with-mic).

---

## Configuring Managed Nodes for Ansible

Once your Vagrant VMs are up and running, you need to configure them to be managed by Ansible.

1.  **Edit the `/etc/hosts` file on your Control Node:**
    On your local machine (the Ansible control node), edit your `/etc/hosts` file to map the private IP addresses of your Vagrant VMs to their hostnames. This allows Ansible to resolve the hostnames.

    ```bash
    sudo nano /etc/hosts
    ```
    Add entries similar to these (adjust IPs and hostnames based on your `Vagrantfile`):
    ```text
    192.168.200.10  centos-7
    192.168.200.11  ubuntu-64
    ```

2.  **Set up SSH Keys for Passwordless Login:**
    Ansible primarily uses SSH for communication. To avoid entering passwords repeatedly, set up SSH key-based authentication from your control node to your Vagrant VMs.

    *   **Generate SSH Key (if you don't have one):**
        ```bash
        ssh-keygen -t rsa -b 2048
        ```
        Accept the default location and passphrase (or set one if desired).

    *   **Copy SSH Key to Managed Nodes:**
        Use `ssh-copy-id` to copy your public key to each Vagrant VM. The default user for Vagrant VMs is `vagrant`.
        ```bash
        ssh-copy-id -i ~/.ssh/id_rsa.pub vagrant@ubuntu-64
        ssh-copy-id -i ~/.ssh/id_rsa.pub vagrant@centos-7
        ```

3.  **Configure Passwordless Sudo on Managed Nodes:**
    For many Ansible tasks, you'll need root privileges. Configure the `vagrant` user on each managed node to use `sudo` without a password.

    *   **SSH into each VM:**
        ```bash
        ssh vagrant@ubuntu-64
        ```
    *   **Edit the sudoers file:**
        ```bash
        sudo visudo
        ```
    *   **Add the following line at the end of the file:**
        ```text
        vagrant ALL=(ALL) NOPASSWD: ALL
        ```
        Repeat this process for `centos-7` (and any other VMs).

---

With your Vagrant lab set up and managed nodes configured for passwordless SSH and sudo, you are ready to install Ansible on your control node and start automating! Refer to the [Ansible Installation](installation.md) guide for the next steps.

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

You have successfully set up your Ansible control node within a Vagrant VM and configured your inventory. You are now ready to explore [Ansible Playbooks](ansible-server/03-playbook.md).