# ManjaroWSL
Manjaro on WSL2 (Windows 10 FCU or later)
based on [wsldl](https://github.com/yuk7/wsldl)

![screenshot](https://raw.githubusercontent.com/sileshn/ManjaroWSL/main/img/screenshot.png)

[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg?style=flat-square)](http://makeapullrequest.com)
![License](https://img.shields.io/github/license/yosukes-dev/FedoraWSL.svg?style=flat-square)

## 💻 Requirements
* Windows 10 1709 Fall Creators Update 64bit or later.
* Windows Subsystem for Linux feature is enabled.

## Install
1. [Download](https://github.com/sileshn/ManjaroWSL/releases/latest) installer zip
2. Extract all files in zip file to same directory
3. Run Manjaro.exe to Extract rootfs and Register to WSL

**Note:**
Exe filename is using the instance name to register. If you rename it you can register with a diffrent name and have multiple installs.

If you want to use WSL2 after install, convert it with the following command.
```dos
wsl --set-version Manjaro 2
```

You can also set wsl2 as default. Use the command below before running Manjaro.exe.
```dos
wsl --set-default-version 2
```

## How-to-Use(for Installed Instance)
#### exe Usage
```
Usage :
    <no args>
      - Open a new shell with your default settings.

    run <command line>
      - Run the given command line in that distro. Inherit current directory.

    runp <command line (includes windows path)>
      - Run the path translated command line in that distro.

    config [setting [value]]
      - `--default-user <user>`: Set the default user for this distro to <user>
      - `--default-uid <uid>`: Set the default user uid for this distro to <uid>
      - `--append-path <on|off>`: Switch of Append Windows PATH to $PATH
      - `--mount-drive <on|off>`: Switch of Mount drives
      - `--default-term <default|wt|flute>`: Set default terminal window

    get [setting]
      - `--default-uid`: Get the default user uid in this distro
      - `--append-path`: Get on/off status of Append Windows PATH to $PATH
      - `--mount-drive`: Get on/off status of Mount drives
      - `--wsl-version`: Get WSL Version 1/2 for this distro
      - `--default-term`: Get Default Terminal for this distro launcher
      - `--lxguid`: Get WSL GUID key for this distro

    backup [contents]
      - `--tgz`: Output backup.tar.gz to the current directory using tar command
      - `--reg`: Output settings registry file to the current directory

    clean
      - Uninstall the distro.

    help
      - Print this usage message.
```

#### Just Run exe
```cmd
>{InstanceName}.exe
[root@PC-NAME user]#
```

#### Run with command line
```cmd
>{InstanceName}.exe run uname -r
4.4.0-43-Microsoft
```

#### Run with command line with path translation
```cmd
>{InstanceName}.exe runp echo C:\Windows\System32\cmd.exe
/mnt/c/Windows/System32/cmd.exe
```

#### Change Default User(id command required)
```cmd
>{InstanceName}.exe config --default-user user

>{InstanceName}.exe
[user@PC-NAME dir]$
```

#### Set "Windows Terminal" as default terminal
```cmd
>{InstanceName}.exe config --default-term wt
```

## How to setup

Open Manjaro.exe and run the following commands.
```dos
passwd
useradd -m -G wheel -s /bin/bash <username>
passwd <username>
exit
```
Execute the command below in a windows cmd terminal from the directory where Manjaro.exe is installed.
```dos
>Manjaro.exe config --default-user <username>
```

## How to uninstall instance
```dos
>Manjaro.exe clean

```

## How to build

#### Prerequisites

Docker, tar, zip, unzip need to be installed.

```dos
git clone git@gitlab.com:sileshn/ManjaroWSL.git
cd ManjaroWSL
make

```
Copy the Manjaro.zip file to a safe location and run the command below to clean.
```dos
make clean

```
