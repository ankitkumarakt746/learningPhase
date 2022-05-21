# SSH (Secure Shell)
<br>


## Overview
- Network protocol for creating a secure connection to a remote machine over a network.
- Works on TCP over port 22
<br>


## Installation
- Step 1: Install package
    For RHEL8:  cmd$ sudo dnf install openssh-server -y
    For Ubuntu: cmd$ sudo apt install openssh-server

- Step 2: Start and enable daemon
    cmd$ sudo systemctl start sshd
    cmd$ sudo systemctl enable sshd

- Step 3: Open SSH port 22 to allow incoming traffic
    cmd$ sudo firewall-cmd --zone=public --permanent --add-service=ssh
    cmd$ sudo firewall-cmd --reload
<br>


## Passwordless SSH connection setup
- Step 1: Check for existing key pair. Look for id\_rsa.pub, id\ecdsa.pub, id\_ed25519.pub  
    cmd$ ls -al ~/.ssh
  Look for id\_rsa.pub, id\ecdsa.pub, id\_ed25519.pub
  If any of the above files are present then jump to Step 3.

- Step 2: Generate new key pair
    cmd$ ssh-keygen

- Step 3: Upload SSH key to the remote machine (say 192.168.1.50)
    cmd$ ssh-copy-id user@192.168.1.50

- Step 4: Login remotely
    cmd$ ssh user@192.168.1.50
