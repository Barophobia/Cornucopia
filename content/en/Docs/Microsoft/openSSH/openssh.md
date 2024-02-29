+++
title = "Installing and configuring OpenSSH"
chapter = true
+++

# OpenSSH Windows

With the addition of windows server 2019 you can now install the openssh component through the server manager features.

'Add Roles & Features' > 'OpenSSH Server'

This will install the OpenSSH Server component and will allow you to edit the config and listen on the relevant port

**Useful locations:**

sshd_config
%programdata%\ssh

sshd executables
C:\Windows\System32\OpenSSH

**Debugging sshd**

To start sshd in debug mode type 'sshd -d' into powershell, this will give you mroe output in the console.

**Turning on logs**

To turn on logs you will need to remove the # before the log config in the ssh_config file located inside %Programdata%\ssh the logs will then go into %programdata%\ssh\logs.

**Fixes:**

**No Service inside the services applet**

If you cannot see the OpenSSH Server process inside the services applet you may need to create your own.

Using CMD:

sc.exe create "OpenSSH Server" C:\Windows\System32\OpenSSH\sshd.exe

**sshd Service will not start**

If the sshd service won't start it may be to do with the security permissions set on the %Programdata%/ssh folder.
There should only be 2 users that have permissions to the SSH folder (SYSTEM & Administrators) outside of the listed 2 the service will not start so remove the permissions and try to start the service.



