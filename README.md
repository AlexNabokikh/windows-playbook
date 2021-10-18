# Windows Ansible Playbook

[![CI][badge-gh-actions]][link-gh-actions]

This playbook installs and configures most of the software I use on my Windows 11 machine for software development.

## Installation

### Prepare your Windows host ⏲

Copy and paste the code below into your PowerShell terminal to get your Windows machine ready to work with Ansible.

```powershell
[Net.ServicePointManager]::SecurityProtocol = [Net.SecurityProtocolType]::Tls12
$url = "https://raw.githubusercontent.com/AlexNabokikh/windows-playbook/master/setup.ps1"
$file = "$env:temp\setup.ps1"

(New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)
powershell.exe -ExecutionPolicy ByPass -File $file -Verbose
```

### Ansible Control node 🕹

1. [Install Ansible](https://docs.ansible.com/ansible/latest/installation_guide/index.html):

    1. Upgrade Pip: `sudo pip3 install --upgrade pip`
    2. Install Ansible: `pip3 install ansible`

2. Clone or download this repository to your local drive.
3. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible collections.
4. Add the IP address and credentials of your Windows machine into the `inventory` file
5. Run `ansible-playbook main.yml` inside this directory.

### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags using `ansible-playbook` `--tags` flag. The tags available are `choco`, `desktop`, `explorer`, `taskbar`, `hostname`.

```sh
ansible-playbook main.yml --tags "choco,explorer"
```

## Overriding Defaults

You can override any of the defaults configured in `default.config.yml` by creating a `config.yml` file and setting the overrides in that file. For example, you can customize the installed packages and apps with something like:

```yaml
choco_installed_packages:
  - googlechrome
  - git
  - golang
```

## Included Applications / Configuration (Default)

Packages (installed with Chocolatey):

- 7zip
- adobereader
- auto-dark-mode
- awscli
- capture2text
- choco-cleaner
- choco-upgrade-all-at-startup
- Firefox
- git
- golang
- jre8
- kubernetes-cli
- microsoft-windows-terminal
- nmap
- powertoys
- python3
- rufus
- telegram
- terraform
- vlc
- vscode
- winmtr-redux
- zoom

## Author

This project was created by [Alexander Nabokikh](https://www.linkedin.com/in/nabokih/) (originally inspired by [geerlingguy/mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook)).

[badge-gh-actions]: https://github.com/AlexNabokikh/windows-playbook/actions/workflows/ci.yml/badge.svg?event=push
[link-gh-actions]: https://github.com/AlexNabokikh/windows-playbook/actions/?query=workflow%3ACI
