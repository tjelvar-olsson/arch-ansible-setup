# arch-ansible-setup
Ansible script for configuring Arch linux installation. Tailored for the Rasberry Pi.

Install prerequisite packages:

```bash
pacman -Syu
pacman -S git
pacman -S ansible
pacman -S ntp
```

Set the time.

```bash
systemctl enable ntpd
systemctl start ntpd
```

Sort out passwordless ssh.

```bash
ssh-keygen
cd .ssh
cat id_rsa.pub >> authorized_keys
```


Run ansible.

```bash
ansible-playbook -i hosts playbook.yml --extra-vars="user_name=alice"
```

##TODO

1. Add bashrc role (lynx, rm aliases)
2. Add font configuration (ubuntu)
3. Add login manager
