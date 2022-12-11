# Windows Ansible Playbook

![Logo](files/logo.png)

![badge-gh-actions]
![badge-windows-10]
![badge-windows-11]
![badge-license]

This playbook installs and configures most of the software I use on my Windows 11 machine for software development.

## Contents

- [Playbook capabilities](#playbook-capabilities)
- [Installation](#installation)
- [Windows host prerequisites installation](#prepare-your-windows-host-)
- [Ansible control node prerequisites installation](#ansible-control-node-)
- [Running a specific set of tagged tasks](#running-a-specific-set-of-tagged-tasks)
- [Overriding Defaults](#overriding-defaults)
- [Included Applications / Configuration (Default)](#included-applications--configuration-default)
- [Available Parameters](#available-parameters)

## Playbook capabilities

> **NOTE:** The Playbook is fully configurable. You can skip or reconfigure any task by [Overriding Defaults](#overriding-defaults).

- **Software**
  - Ensures Bloatware is removed (see default config for a complete list of Bloatware).
  - Ensure software and packages selected by the user are installed via Chocolatey.
- **Windows apps & features**
  - Ensures the Optional Windows Features chosen by the user are installed and enabled.
  - Ensures the WSL2 distro selected by the user is installed and enabled.
  - Ensures set by user volumes are defragmented (in parallel).
- **Windows Settings**
  - **Explorer**
    - Ensures Explorer includes the file extension in file names.
    - Ensures Explorer opens itself to the Computer view.
    - Ensures the Ribbon menu is disabled in Windows Explorer.
    - Ensures Right-click Context Menu enabled (Windows 11).
  - **Start Menu**
    - Ensures Automatic Install of Suggested Apps disabled.
    - Ensures the "App Suggestions" in the Start menu is disabled.
    - Ensures the "tips" popup Windows disabled.
    - Ensures 'Windows Welcome Experience' is disabled.
  - **Taskbar**
    - Ensures 'Search' unpinned from Taskbar.
    - Ensures Task View, Chat, and Cortana are unpinned from Taskbar.
    - Ensures 'News and Interests' unpinned from Taskbar.
    - Ensures 'People' unpinned from Taskbar.
    - Ensures 'Edge', 'Store' and other built-in shortcuts unpinned from Taskbar.
  - **Desktop**
    - Ensure Desktop icons are removed.
  - **General**
    - Ensure configured hostname selected by the user is assigned.
    - Ensure remote desktop services are configured.
    - Ensure the sound scheme is set to 'No sounds'.
    - Ensure the power plan selected by the user is assigned.
    - Ensure Windows updates are selected by the user installed.
    - Ensures mouse acceleration is disabled.
- **Terminal Settings**
  - Ensures [oh-my-posh](https://ohmyposh.dev/) with the theme chosen by the user is set as a default PowerShell theme engine.

## Installation

### Prepare your Windows host ⏲

#### **This playbook was tested on Windows 10 2004 and Windows 11 21H2 (Pro, Ent). Other versions may work but have not tried.**

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

   1. Upgrade Pip: `pip3 install --upgrade pip`
   2. Install Ansible: `pip3 install ansible`

2. Clone or download this repository to your local drive.
3. Run `ansible-galaxy install -r requirements.yml` inside this directory to install required Ansible collections.
4. Add the IP address and credentials of your Windows machine into the `inventory` file
5. Run `ansible-playbook main.yml` inside this directory.

### Running a specific set of tagged tasks

You can filter which part of the provisioning process to run by specifying a set of tags using `ansible-playbook` `--tags` flag. The tags available are `choco` , `debloat` , `desktop` , `explorer` , `fonts` , `hostname` , `mouse` , `power` , `sounds` , `start_menu` , `taskbar` , `updates` , `windows_features` , `wsl` .

```sh
ansible-playbook main.yml --tags "choco,wsl"
```

## Overriding Defaults

**NOTE:** You can override any of the defaults configured in `default.config.yml` by creating a `config.yml` file and setting the overrides in that file. For example, you can customize the installed packages and enable/disable specific tasks with something like:

```yaml
configure_hostname: true
custom_hostname: myhostname

install_windows_updates: true
update_categories:
  - Critical Updates
  - Security Updates
  - * # Installs all updates

choco_installed_packages:
  # installs latest version of the Google Chrome while ignoring the package checksum
  - name: googlechrome
    state: latest
    choco_args: --ignorechecksum
  # installs 2.37.1 version of the git
  - name: git
    version: "2.37.1"
  # installs GO, but won't update it
  - golang

install_fonts: true
installed_nerdfonts:
  - Meslo

install_ohmyposh: true
ohmyposh_theme: agnoster

install_windows_features: true
windows_features:
  Microsoft-Hyper-V: true

install_wsl2: true
wsl2_distribution: wsl-archlinux

remove_bloatware: true
bloatware:
  - Microsoft.Messaging
```

## Included Applications / Configuration (Default)

Packages (installed with Chocolatey):

- adobereader
- auto-dark-mode
- awscli
- Firefox
- git
- golang
- jre8
- kubernetes-cli
- microsoft-windows-terminal
- peazip
- powertoys
- python3
- sharex
- telegram
- terraform
- vlc
- vscode
- zoom

## Available Parameters

| Name                       | Description                                                                                                      | Type         | Default                                                                                                                            |
| -------------------------- | ---------------------------------------------------------------------------------------------------------------- | ------------ | ---------------------------------------------------------------------------------------------------------------------------------- |
| configure_hostname         | (Optional) Whether or not to set a custom hostname.                                                              | `bool`       | `false`                                                                                                                            |
| custom_hostname            | (Optional) The hostname to set for the computer.                                                                 | `string`     | `windows-ansible`                                                                                                                  |
| install_windows_updates    | (Optional) Whether or not to install Windows updates.                                                            | `bool`       | `true`                                                                                                                             |
| update_categories          | (Optional) A list of categories to install updates from. The value \* will match all categories.                 | `list`       | `["CriticalUpdates", "SecurityUpdates", "UpdateRollups"]`                                                                          |
| windows_updates_reboot     | (Optional) Whether or not to reboot the host if it is required and continue to install updates after the reboot. | `bool`       | `true`                                                                                                                             |
| remove_bloatware           | (Optional) Whether or not to uninstall Windows bloatware.                                                        | `bool`       | `true`                                                                                                                             |
| bloatware                  | (Optional) A list of applications (bloatware) to be uninstalled                                                  | `list`       | [full_list](https://github.com/AlexNabokikh/windows-playbook/blob/8be81399018d151e5f4f5ea08034fc4bd0ad30da/default.config.yml#L85) |
| choco_installed_packages   | (Required) A list of Chocolatey packages to be installed.                                                        | `list`       | [full_list](#included-applications--configuration-default)                                                                         |
| state (chocolatey)         | (Optional) State of the package on the system. (present, latest)                                                 | `string`     | `present`                                                                                                                          |
| version (chocolatey)       | (Optional) Specific version of the package to be installed.                                                      | `string`     | `omit`                                                                                                                             |
| choco_args (chocolatey)    | (Optional) Additional parameters to pass to choco.exe.                                                           | `string`     | `omit`                                                                                                                             |
| install_windows_features   | (Optional) Whether or not to install Windows features.                                                           | `bool`       | `false`                                                                                                                            |
| windows_features           | (Optional) A list of dicts with Windows features to be installed.                                                | `list(dict)` | `Microsoft-Hyper-V: true`                                                                                                          |
| install_wsl2               | (Optional) Whether or not to install Windows Subsystem for Linux.                                                | `bool`       | `true`                                                                                                                             |
| wsl2_distribution          | (Optional) The valid name of Linux distribution that will be installed.                                          | `string`     | `wsl-ubuntu-2004`                                                                                                                  |
| install_fonts              | (Optional) Whether or not to install [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/).                     | `bool`       | `true`                                                                                                                             |
| installed_nerdfonts        | (Optional) A list of [Nerd Fonts](https://github.com/ryanoasis/nerd-fonts/) to be installed.                     | `list`       | `["FiraCode", "FantasqueSansMono"]`                                                                                                |
| install_ohmyposh           | (Optional) Whether or not to [Oh My Posh](https://ohmyposh.dev/).                                                | `bool`       | `true`                                                                                                                             |
| configure_explorer         | (Optional) Whether or not to configure Windows Explorer with sane defaults.                                      | `bool`       | `true`                                                                                                                             |
| configure_taskbar          | (Optional) Whether or not to configure Windows TaskBar with sane defaults.                                       | `bool`       | `true`                                                                                                                             |
| configure_start_menu       | (Optional) Whether or not to configure Windows Start menu with sane defaults.                                    | `bool`       | `true`                                                                                                                             |
| set_sound_scheme           | (Optional) Whether or not to set default Windows Sound Scheme to "No Sounds".                                    | `bool`       | `true`                                                                                                                             |
| disable_mouse_acceleration | (Optional) Whether or not to disable mouse acceleration.                                                         | `bool`       | `true`                                                                                                                             |
| remote_desktop_enabled     | (Optional) Whether or not enable Remote Desktop.                                                                 | `bool`       | `true`                                                                                                                             |
| remove_desktop_icons       | (Optional) Whether or not remove desktop icons (\*.lnk files only).                                              | `bool`       | `false`                                                                                                                            |
| defrag_volumes             | (Optional) Whether or not to perform disk defragmentation.                                                       | `bool`       | `true`                                                                                                                             |
| include_volumes            | (Optional) A list of volumes to be defragmented.                                                                 | `list`       | `["C"]`                                                                                                                            |
| change_power_plan          | (Optional) Whether or not change Power Plan.                                                                     | `bool`       | `true`                                                                                                                             |
| power_plan                 | (Optional) Choose a power plan (high_performance, balanced, power_saver).                                        | `string`     | `high_performance`                                                                                                                 |

## Author

This project was created by [Alexander Nabokikh](https://www.linkedin.com/in/nabokih/) (initially inspired by [geerlingguy/mac-dev-playbook](https://github.com/geerlingguy/mac-dev-playbook)).

## License

This software is available under the following licenses:

- **[MIT](https://github.com/AlexNabokikh/windows-playbook/blob/master/LICENSE)**

[badge-gh-actions]: https://github.com/AlexNabokikh/windows-playbook/actions/workflows/release.yaml/badge.svg
[badge-windows-11]: https://img.shields.io/badge/OS-Windows%2011%2021H2-blue
[badge-windows-10]: https://img.shields.io/badge/OS-Windows%2010%2020H2-blue
[badge-license]: https://img.shields.io/badge/License-MIT-informational
