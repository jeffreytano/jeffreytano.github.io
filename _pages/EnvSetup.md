---
layout: single
title: "Environment setup"
permalink: /EnvSetup/
classes: wide
sidebar:
  nav: Learning
---

https://learn.microsoft.com/en-us/powershell/scripting/learn/remoting/ssh-remoting-in-powershell-core?view=powershell-7.3

https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=powershell

## Enable SSH connection

1. Install PowerShell v7 [Download Link](https://learn.microsoft.com/en-us/powershell/scripting/install/installing-powershell-on-windows?view=powershell-7.3){: .btn .btn--info}{:target="\_blank"}
2. Follow steps on [OpenSSH](https://learn.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse?tabs=powershell){: .btn .btn--info}
3. Open PowerShell as admin

   ```console
   Get-WindowsCapability -Online | Where-Object Name -like 'OpenSSH*'
   ```

   If OpenSSH Client and Server are not installed. Result will be as follows:

   ```console
   Name  : OpenSSH.Client~~~~0.0.1.0
   State : NotPresent

   Name  : OpenSSH.Server~~~~0.0.1.0
   State : NotPresent
   ```

4. Then install the Client and Server

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

5. ```
   Start-Service sshd

   Set-Service -Name sshd -StartupType 'Automatic'

   if (!(Get-NetFirewallRule -Name "OpenSSH-Server-In-TCP" -ErrorAction SilentlyContinue | Select-Object Name, Enabled)) {
       Write-Output "Firewall Rule 'OpenSSH-Server-In-TCP' does not exist, creating it..."
       New-NetFirewallRule -Name 'OpenSSH-Server-In-TCP' -DisplayName 'OpenSSH Server (sshd)' -Enabled True -Direction Inbound -Protocol TCP -Action Allow -LocalPort 22
   } else {
       Write-Output "Firewall rule 'OpenSSH-Server-In-TCP' has been created and exists."
   }
   ```

\*\*When you clone repository from github by SSH, output like this may happens

```
The authenticity of host 'servername (10.00.00.001)' can't be established.
ECDSA key fingerprint is SHA256:(<a large string>).
Are you sure you want to continue connecting (yes/no)?
```

Just type "yes" and it will work fine

## Docker

## Linux
