# Ansible Vagrant Lab

## Control node requirement

For the control node, you can use any machine with Python 2.7 or Python 3.5 (or higher) installed. The Ansible installation is simple and depends on the OS of your control node, see [Ansible document](https://docs.ansible.com/ansible/2.9/installation_guide/index.html) for installation.

### Managed node requirement

For managed nodes, Ansible makes a connection over SSH, Python and SSH client is required.

### Requirements of this lab

1. VMware or Virtual box
2. Vagrant

### Using Vagrant to Set Up a Test Server

Vagrant is an excellent open-source tool for managing virtual machines. You can use Vagrant to boot a Linux virtual machine inside your laptop, and you can use that as a test server. I'm using Vagrant for my lab set-up, the process is simple as below:

1. Go to the [Vagrant website](https://www.vagrantup.com/) and download vagrant and install it on your machine. For more details see [Introduction to Vagrant](https://ayushsharma.in/2021/08/introduction-to-vagrant) and [Quick Start Guide](https://learn.hashicorp.com/tutorials/vagrant/etting-started-index?in=vagrant/getting-started).

2. [Virtual box](https://www.virtualbox.org/wiki/Downloads).
3. [Vagrant file](https://github.com/sydasif/ansible-lab/blob/master/Vagrantfile).

Create a directory in your machine and copy the vagrant file from the repo. In my case, I, create a directory in Document, named vagrant (name can be
anything). Open Powershell/Bash and navigate to the concerning directory and boot the Vagrant.

### To boot the vagrant devices

```vagrant up``` will create and boot the below device's.

1. ubuntu
2. centos

Command after booting to check the status of devices:

```console
vagrant status
```

Use ```vagrant ssh ubuntu-64``` command to ssh into a device and check ping to the other device. If any error with ssh connection, see this [Permission denied](https://stackoverflow.com/questions/36300446/ssh-permission-denied-publickey-gssapi-with-mic) guide on StackOverflow.

#### Configuring Ansible Client

I have two Vagrant hosts ubuntu-64, centos-7 and Ansible control node(my own pc). On the control node (Ubuntu), edit the host's file for IP to name resolution.

```console
sudo nano /etc/hosts
```

After opening the file add below IP and host-name.

```console
192.168.200.10  centos-7
192.168.200.11  ubuntu-64
```

Create SSH key on Ansible control node (Ubuntu) with below and accept the defaults.

```console
ssh-keygen
```

list the keys to verify with the *ls .ssh* command, and copy the key to the client's machine.

```console
ssh-copy-id -i .ssh/id_rsa.pub ubuntu-64
ssh-copy-id -i .ssh/id_rsa.pub centos-7
```

Now ssh to Ubuntu-64, and configure the managed host, so that it doesn't require a password to get *sudo* level access.

```console
ssh ubuntu
sudo visudo
```

Go to the bottom of the file and add this line as below:

```console
vagrant ALL=(ALL) NOPASSWD: ALL
```

Also, configure centos so that it doesn't require a password to get root-level access.

```console
ssh centos-7
su -
sudo visudo
```

Go to the bottom of the file and add this line as below:

```console
vagrant ALL=(ALL) NOPASSWD: ALL
```

### Ansible installation on Ubuntu

```console
sudo apt update
sudo apt install software-properties-common
sudo apt-add-repository ppa:ansible/ansible-2.9
sudo apt install ansible -y
```

### Installing Ansible with pip

```console
sudo apt update
sudo apt install python3 python3-pip git
pip3 install ansible
```

To test Ansible Installation, run the below commands:

```console
ansible --version
ansible localhost -m ping
```

### Inventory Set-Up

Ansible inventory files define managed nodes that ad-hoc command/playbooks can be run against. I'm creating inventory in the ansible default location (
/etc/ansible/hosts).

```console
sudo nano /etc/ansible/hosts
```

Create groups and add hosts to the group.

```console
[ubuntu]
ubuntu-64

[centos]
centos-7

[linux:children]
ubuntu
centos
```

The lab setup is now completed.
