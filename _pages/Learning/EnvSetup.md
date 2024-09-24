---
layout: single
title: "Environment setup"
permalink: /EnvSetup/
classes: wide
sidebar:
  nav: Learning
---

## Enable SSH connection

1. Install PowerShell v7 [Download Link](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3){: .btn .btn--info}{:target="\_blank"}
2. Follow steps on [OpenSSH](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=powershell){: .btn .btn--info}
   Open PowerShell as admin

   ```console
   Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
   ```

   If OpenSSH Client and Server are not installed, result will be as follow:

   ```console
   Name  : OpenSSH.Client~~~~0.0.1.0
   State : NotPresent

   Name  : OpenSSH.Server~~~~0.0.1.0
   State : NotPresent
   ```

3. Then install the Client and Server

   ```console
   Add-WindowsCapability -Online -Name OpenSSH.Client~~~~0.0.1.0
   Add-WindowsCapability -Online -Name OpenSSH.Server~~~~0.0.1.0
   ```

   It is expected to have output like this for both

   ```
   Path          :
   Online        : True
   RestartNeeded : False
   ```

4. ```
   Start-Service sshd

   Set-Service -Name sshd -StartupType 'Automatic'

   if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue | Select-Object Name, Enabled)) {
       Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..."
       New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
   } else {
       Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."
   }
   ```

### Generating SSH key for specific hardware

1. **Open PowerShell and run below to generate SSH key**

```
ssh-keygen
```

This command will ask something like directory to save ssh-key and passphrase, you can just keep pressing enter for default directory.

```
Generating public/private rsa key pair.
Enter file in which to save the key (C:\Users\Hairo/.ssh/id_rsa):
Created directory 'C:\Users\Hairo/.ssh'.
Enter passphrase (empty for no passphrase):
Enter same passphrase again:
Your identification has been saved in C:\Users\Hairo/.ssh/id_rsa.
Your public key has been saved in C:\Users\Hairo/.ssh/id_rsa.pub.
The key fingerprint is:
```

   You can find your SSH key in C:/Users/@username/.ssh/ \
   default name is id_rsa

2. **Open the id_rsa.pub with any text editor and copy the entire SSH key**

   Go to your github account → Setting → SSH and GPG keys → New SSH key. Paste the key into `Key` textbox, choose `Authentication Key` and define any title for it.

3. Try cloning repository with SSH link**

   Go to your repository, copy the SSH links and run

```
git clone {your github ssh link}
```

When you clone repository from github by SSH, output like this may happens

```
The authenticity of host 'servername (10.00.00.001)' can't be established.
ECDSA key fingerprint is SHA256:(<a large string>).
Are you sure you want to continue connecting (yes/no)?
```

   Just type "yes" and it will work fine

## Docker

https://docs.docker.com/language/nodejs/develop/ maybe this one?

## Linux
