# kali-pentest-machine-setup

This repo contains Ansible playbooks to install extra tools on top of Kali Linux.

## Howto?

01. Install git and ansible

```zsh
sudo apt update
sudo apt install git ansible -y
```

02. Clone this repo

```zsh
git clone https://github.com/fazlearefin/kali-pentest-machine-setup.git
cd kali-pentest-machine-setup
```

03. Run the ansible playbook to install the extra tools

Enter the password for the user (`kali`) when asked for a password

```zsh
ansible-playbook -vv -i hosts -e "local_username=$(id -un)" -K main.yml
```

---

## Kali Linux Metapackages

[List of metapackages](https://www.kali.org/docs/general-use/metapackages/)
