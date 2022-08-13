# kali-ctf-machine-setup

This repo contains Ansible playbooks to install extra tools on top of Kali Linux for CTF activities.

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
# install WITHOUT docker vulnerable images
ansible-playbook -vv -i hosts -e "{ setup_vuln_docker_images: false }" -e "local_username=$(id -un)" -K main.yml

# install WITH docker vulnerable images
ansible-playbook -vv -i hosts -e "{ setup_vuln_docker_images: true }" -e "local_username=$(id -un)" -K main.yml
```

---

## Kali Linux Useful Links

- [Kali Linux Metapackages](https://www.kali.org/docs/general-use/metapackages/)
- [Kali Tools](https://www.kali.org/tools/)
- [Kali's Default Credentials](https://www.kali.org/docs/introduction/default-credentials/)
