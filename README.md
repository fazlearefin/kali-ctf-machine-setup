# kali-ctf-machine-setup

This repo contains Ansible playbooks to install extra tools on top of Kali Linux for CTF (Capture The Flag) and pentest activities.

These tools are useful when playing CTF in platforms such as [Hack The Box](https://www.hackthebox.com/), [TryHackMe](https://tryhackme.com/), etc.

## Howto?

### 0. Setup Kali Linux

It is assummed that you have a plain vanilla installation of Kali Linux. This README is tailored for [Kali virtual machine images](https://www.kali.org/get-kali/#kali-virtual-machines)

### 1. Upgrade packages

This step is optional as the ansible playbook takes care of this. But it is highly recommended you upgrade all the installed packges at this stage to avoid issues later.

```zsh
sudo apt update
sudo apt full-upgrade -y
```

### 2.   Install git and ansible

```zsh
sudo apt update
sudo apt install git ansible -y
```

### 3. Clone this repo

```zsh
git clone https://github.com/fazlearefin/kali-ctf-machine-setup.git
cd kali-ctf-machine-setup
```

### 4. Run the ansible playbook to install the extra tools

Enter the password for the user (`kali`) when asked for a password (your user ID might be different if it is a custom installation).

Run one of the commands below depending on whether you want the vulnerable docker images to be pulled or not.

#### Install WITHOUT docker vulnerable images

```zsh
ansible-playbook -vv -i localhost, -e "{ setup_vuln_docker_images: false }" -e "local_username=$(id -un)" -K main.yml
```

#### Install WITH docker vulnerable images

```zsh
ansible-playbook -vv -i localhost, -e "{ setup_vuln_docker_images: true }" -e "local_username=$(id -un)" -K main.yml
```

---

## Bundled docker vulnerable images

*Docker vulnerable images* are docker containers to running deliverately vulnerable services. The following vulnerable images are installed so that you can practice within your own Kali installation:

- [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- [OWASP WebGoat](https://owasp.org/www-project-webgoat/)

### Running the vulnerable docker images

#### OWASP Juice Shop

```zsh
docker run --rm -d -p 3000:3000 --name juice-shop bkimminich/juice-shop
# use web browser to go to http://localhost:3000 in Kali host
```

#### OWASP WebGoat

```zsh
docker run --rm -it -p 127.0.0.1:8080:8080 -p 127.0.0.1:9090:9090 -e TZ=UTC --name webgoat webgoat/webgoat
# use web browsser to go to http://127.0.0.1:8080/WebGoat in Kali host
```

---

## Additional Git Repos

Additional git repos cloned locally at these locations:

- [`/opt/GitTools`](https://github.com/internetwache/GitTools): A repository with 3 tools for pwn'ing websites with .git repositories available
- [`/opt/zphisher`](https://github.com/htr-tech/zphisher): An automated phishing tool with 30+ templates
- [`/opt/vulhub`](https://github.com/vulhub/vulhub): Pre-Built Vulnerable Environments Based on Docker-Compose
- [`/opt/privesc-scripts/LinEnum`](https://github.com/rebootuser/LinEnum): Scripted Local Linux Enumeration & Privilege Escalation Checks
- [`/opt/privesc-scripts/linux-exploit-suggester`](https://github.com/The-Z-Labs/linux-exploit-suggester): Linux privilege escalation auditing tool
- [`/opt/privesc-scripts/linux-smart-enumeration`](https://github.com/diego-treitos/linux-smart-enumeration): Linux enumeration tool for pentesting and CTFs with verbosity levels Topics
- [`/opt/privesc-scripts/PEASS-ng`](https://github.com/carlospolop/PEASS-ng): PEASS - Privilege Escalation Awesome Scripts SUITE (with colors)
- [`/opt/WEF`](https://github.com/D3Ext/WEF): Wi-Fi Exploitation Framework

---

## Kali Linux Useful Links

- [Kali Tools](https://www.kali.org/tools/)
- [Kali Linux Metapackages](https://www.kali.org/tools/kali-meta/)
- [Kali's Default Credentials](https://www.kali.org/docs/introduction/default-credentials/)

## Other Useful Links

- **[HackTricks](https://book.hacktricks.xyz/)** ⭐
- **[HackTricks Cloud](https://cloud.hacktricks.xyz/)** ⭐
- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/)
- [OWASP Web Security Testing Guide](https://owasp.org/www-project-web-security-testing-guide/latest/)
- [GTFOBins](https://gtfobins.github.io/)
- [CyberChef](https://gchq.github.io/CyberChef/) - Encode/decode data
- [CrackStation](https://crackstation.net/) - Hash Rainbow List
- [Reverse Shell Generator](https://www.revshells.com/)
- [CI/CD Goat](https://github.com/cider-security-research/cicd-goat)
- [h4cker](https://github.com/The-Art-of-Hacking/h4cker)

---

## Donations

If you think my work helped you in some way saving you time and effort, I am happy to receive any amount of donation. However, the code in this repo is completely free.

Bitcoin (BTC): `bc1qzlhpm94vtk2ht67etdutzcy2g5an5v6g36tp0m`
