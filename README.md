# kali-ctf-machine-setup

This repo contains Ansible playbooks to install extra tools on top of Kali Linux for CTF activities.

These tools are useful when playing CTF in platforms such as [Hack The Box](https://www.hackthebox.com/), [TryHackMe](https://tryhackme.com/), etc.

## Howto?

### 0. Kali Linux Installation

It is assummed that you have a plain vanilla installation of Kali Linux. This README is tailored for [Kali virtual machine images](https://www.kali.org/get-kali/#kali-virtual-machines)


### 1.   Install git and ansible

```zsh
sudo apt update
sudo apt install git ansible -y
```

### 2. Clone this repo

```zsh
git clone https://github.com/fazlearefin/kali-pentest-machine-setup.git
cd kali-pentest-machine-setup
```

### 3. Run the ansible playbook to install the extra tools

Enter the password for the user (`kali`) when asked for a password

```zsh
# install WITHOUT docker vulnerable images
ansible-playbook -vv -i hosts -e "{ setup_vuln_docker_images: false }" -e "local_username=$(id -un)" -K main.yml

# install WITH docker vulnerable images
ansible-playbook -vv -i hosts -e "{ setup_vuln_docker_images: true }" -e "local_username=$(id -un)" -K main.yml
```

---

## Bundled docker vulnerable images

*Docker vulnerable images* are docker containers to running deliverately vulnerable services. The following vulnerable images are installed so that you can practice within your own Kali installation:

- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [OWASP WebGoat](https://owasp.org/www-project-webgoat/)

### Running the vulnerable docker images

```zsh
# OWASP Juice Shop
docker run --rm -d -p 3000:3000 --name juice-shop bkimminich/juice-shop
# use web browser to go to http://localhost:3000 in Kali host

# OWASP WebGoat
docker run --rm -it -p 127.0.0.1:8080:8080 -p 127.0.0.1:9090:9090 -e TZ=UTC --name webgoat webgoat/webgoat
# use web browsser to go to http://127.0.0.1:8080/WebGoat in Kali host

```

---

## Kali Linux Useful Links

- [Kali Tools](https://www.kali.org/tools/)
- [Kali Linux Metapackages](https://www.kali.org/tools/kali-meta/)
- [Kali's Default Credentials](https://www.kali.org/docs/introduction/default-credentials/)

## Other Useful Links

- [GTFOBins](https://gtfobins.github.io/)
- [HackTricks](https://book.hacktricks.xyz/)
- [HackTricks Cloud](https://cloud.hacktricks.xyz/)
- [CyberChef](https://gchq.github.io/CyberChef/) - Encode/decode data
- [CrackStation](https://crackstation.net/) - Hash Rainbow List
- [Reverse Shell Generator](https://www.revshells.com/)
- [CI/CD Goat](https://github.com/cider-security-research/cicd-goat)
