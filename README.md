# Ansible setup to create a kvm server
1. Make sure your copy the generated public key in /home/vagrant/.ssh/id_rsa.pub to your a users home folder in the authorized_keys file
2. Then run "ansible-playbook create_server.yml --ask-sudo-pass"
