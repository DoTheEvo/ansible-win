# Ansible Windows

![Logo](https://i.imgur.com/SkSns0O.png)

[Learning ansible?](https://www.youtube.com/watch?v=goclfp6a2IQ&list=PL2_OBreMn7FqZkvMYt6ATmgC0KAGGJNAN)

# Overview

Ansible is an automation platform.<br>
It executes commands from `playbooks` on machines listed in `inventory`.

Open source. Developed by Red Hat.
Written and dependent on python. Uses YAML formatting configuration.
Agent-less, just machines with ssh+python (linux) or
rdp+powershell (windows).<br>
Praised for simplicity.

# Objective

To clone a repo, execute few commands, wait,
BAM! Windonws is suddenly just like you want it.<br>
To have a dedicated place where to write prefered applications, services, settings,..

# How to execute

On windows host 

[ConfigureRemotingForAnsible.ps1](https://github.com/ansible/ansible/blob/devel/examples/scripts/ConfigureRemotingForAnsible.ps1)

    $url = "https://raw.githubusercontent.com/ansible/ansible/devel/examples/scripts/ConfigureRemotingForAnsible.ps1"
    $file = "$env:temp\ConfigureRemotingForAnsible.ps1"

    (New-Object -TypeName System.Net.WebClient).DownloadFile($url, $file)

    powershell.exe -ExecutionPolicy ByPass -File $file

* install ansible and git - `sudo pacman -S ansible git`
* clone this repo - `git clone https://github.com/DoTheEvo/ansible-win.git`
* enter the directory - `cd ansible`
* run the playbooks you want
    * `ansible-playbook -u $USER -K playbook_core.yml`
    * `ansible-playbook -u $USER -K playbook_zsh.yml`
    * `ansible-playbook -u $USER -K playbook_docker.yml`

*extra info:*<br>
the `-K` is short for `--ask-become-pass` to prompt for $USER password

# Playbooks

#### playbook_core.yml


### Local deployment

This is for a local deployment.
Meaning the machine is *changing* itself,
as oppose to more typical ansible use, where you run playbooks on one machine
to *change* 143 virtual machines somewhere on the cloud.

To go from local to remote, edit inventory and remove local entry
and add IP of machines you want to *change*.
