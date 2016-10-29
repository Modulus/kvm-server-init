# Ansible setup to create a kvm server
This ansible collection of playbooks will help you setup a kvm server.

## How to start
1. cd into /vagrant
2. Run "ansible-playbook controller.yml"
3. Make sure your copy the generated public key in /home/vagrant/.ssh/id_rsa.pub to your a users home folder in the authorized_keys file
4. Then run "ansible-playbook create_server.yml --ask-sudo-pass"


*sources*: [Installation guide](https://help.ubuntu.com/lts/serverguide/libvirt.html)
