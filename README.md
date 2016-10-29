# Ansible setup to create a kvm server
This ansible collection of playbooks will help you setup a kvm server. This requires you have an ubuntu server 14.04 or later up and running.
See in inventory/server in this code base before starting anything. This needs the ip address and username to the server before it can provision the kvm-server.

## How to start
1. Run "vagrant up" inside the root foler
2. Run "vagrant ssh"
3. Run "cd /vagrant"
4. Make sure your copy the generated public key in /home/vagrant/.ssh/id_rsa.pub to your a users home folder in the authorized_keys file
5. Then run "ansible-playbook create_server.yml --ask-sudo-pass"


*sources*: [Installation guide](https://help.ubuntu.com/lts/serverguide/libvirt.html)
