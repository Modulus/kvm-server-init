# Ansible setup to create a kvm server
This ansible collection of playbooks will help you setup a kvm server. This requires you have an ubuntu server 14.04 or later up and running.



## Before you start
1. See in inventory/server in this code base before starting anything. This needs the ip address and username to the server before it can provision the kvm-server.
2. Log onto your system and add a ansible user, this user should also be in the sudo group
*.. sudo useradd -G ansible,sudo,libvirtd -m ansible
*.. This user also need the controllers /home/vagrant/.ssh/id_rsa.pub key in the authorized_keys file under /home/ansible/.ssh/authorized_keys on the kvm server.

## How to start
1. Run "vagrant up" inside the root foler
2. Run "vagrant ssh"
3. Run "cd /vagrant"
4. Make sure your copy the generated public key in /home/vagrant/.ssh/id_rsa.pub to your a users home folder in the authorized_keys file
5. Then run "ansible-playbook create_server.yml --ask-sudo-pass"


*sources*: [Installation guide](https://help.ubuntu.com/lts/serverguide/libvirt.html)

### Fix permission error:
=====================
SOLVED: found a way.
Changing /etc/libvirt/qemu.conf to make things work.
Uncomment user/group to work as root.
Then restart libvirtd

1. *First edit the /etc/libvirt/qemu.conf*
```bash
# The user for QEMU processes run by the system instance. It can be
# specified as a user name or as a user id. The qemu driver will try to
# parse this value first as a name and then, if the name doesn't exist,
# as a user id.
#
# Since a sequence of digits is a valid user name, a leading plus sign
# can be used to ensure that a user id will not be interpreted as a user
# name.
#
# Some examples of valid values are:
#
#       user = "qemu"   # A user named "qemu"
#       user = "+0"     # Super user (uid=0)
#       user = "100"    # A user named "100" or a user with uid=100
#
user = "root"

# The group for QEMU processes run by the system instance. It can be
# specified in a similar way to user.
group = "root"

# Whether libvirt should dynamically change file ownership
# to match the configured user/group above. Defaults to 1.
# Set to 0 to disable file ownership changes.
#dynamic_ownership = 1
```

2. *Then restart the libvirtd service*
```bash
[root@dev1 ~]# service libvirtd restart
Stopping libvirtd daemon:                                  [  OK  ]
Starting libvirtd daemon:                                  [  OK  ]
```
