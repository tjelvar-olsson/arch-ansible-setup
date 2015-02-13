# arch-ansible-setup
Ansible script for configuring Arch linux installation. Tailored for the Rasberry Pi.

## Pre-amble

From a clean noobs arch installation, login as root, set the keyboard layout and reset the root password.

```bash
loadkeys uk
passwd
```

Configure the wireless network.

```bash
wifi-menu -o
```

And enable it at boot.

```bash
ls /etc/netctl
netctl enable wlan-network-name
```

Update the system.

```bash
pacman -Syu
```

Install prerequisite packages.

```bash
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
cd
```

Clone this repository.

```bash
git clone https://github.com/tjelvar-olsson/arch-ansible-setup.git
```

Run ansible.

```bash
cd arch-ansible-setup
ansible-playbook -i hosts playbook.yml --extra-vars="user_name=alice"
```

Update the password of the newly created user.

```bash
passwd alice
```

Edit the ``/etc/sudoers`` file using visudo to enable members of the sudo
groups to execute any command.

```bash
visudo
```

Reboot the machine.

```bash
reboot
```

##TODO

- Install and configure less with syntax highlighting
- Extend .bashrc file
- Add vim ftplugin files
