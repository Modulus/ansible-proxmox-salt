# Ansible playbook setup promox
This ansible collection of playbooks will help you setup a salt master. This requires you have a Proxmox server up and running.

## Proxmox
More on proxmox here: [proxmox](https://www.proxmox.com/en/)
Download [proxmox iso](https://www.proxmox.com/en/downloads?task=callelement&format=raw&item_id=211&element=f85c494b-2b32-4109-b8c1-083cca2b7db6&method=download&args[0]=21c9042132e3376765ceafca50271007)

## Before you start
1. See in inventory/server in this code base before starting anything. This needs the ip address and username to the server before it can provision the kvm-server.
2. Log onto your system and add a ansible user, this user should also be in the sudo group
*.. sudo useradd -G sudo -m ansible
*.. on centos usermod -aG wheel ansible
*.. This user also need the controllers /home/vagrant/.ssh/id_rsa.pub key in the authorized_keys file under /home/ansible/.ssh/authorized_keys on the kvm server.

## How to start
1. Run "vagrant up" inside the root foler
2. Run "vagrant ssh"
3. Run "cd /vagrant"
4. Make sure your copy the generated public key in /home/vagrant/.ssh/id_rsa.pub to your a users home folder in the authorized_keys file
5. Then run "ansible-playbook create_server.yml --ask-sudo-pass"


#salt-cloud
1. sudo salt-cloud -F proxmox-provider list_nodes
2. sudo salt-cloud -p proxmox-ubuntu-16.04_micro minion1  -l debug
