# arch-ansible-setup
Ansible script for configuring Arch linux installation.

Install prerequisite packages:

```bash
pacman -S ansible
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

1. Make /usr/share/colors/solarized/files excutable
2. Setup github account
3. Add bashrc role (lynx, rm aliases)
4. Add font configuration (ubuntu)
5. Try re-install
