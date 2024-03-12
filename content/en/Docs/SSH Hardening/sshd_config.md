+++
title = "sshd_config"
weight = 5
chapter = true
pre = "<b> - </b>"
+++

```

############
# BINDINGS #
############

# CHANGE THE PORT NUMBER
# This port should be changed as it is an easy target for script kiddies and brute forcing.
Port 22

# Server Listen Address
# This should be the server's IP Address not 0.0.0.0 to minimise random incoming connections
ListenAddress 0.0.0.0

# Address Family
# IPv4 only, this can be changed to 'any' to allow IPv6 or IPv4
AddressFamily inet

###################
# BANNER SETTINGS #
###################

# Warning Banner
# If the server is internet facing ensure you ommit any identifying information in the banner
Banner /etc/issue.net

################
# CRYPTOGRAPHY #
################

# Define cryptography algorithms to avoid the use of weak algorithms
# AES-CTR and Chacha20-Poly1305 modes have been removed to mitigate the Terrapin attack
#   https://terrapin-attack.com/
# ecdh-sha2-nistp* algorithms have been removed due to concerns around NIST P-curves design, they can be readded if you trust the NSA to design your algorithms
#   https://github.com/jtesta/ssh-audit/issues/213#issuecomment-1774204745
# Remember to Disable small Diffie-Hellman Key Sizes

Ciphers aes256-gcm@openssh.com,aes128-gcm@openssh.com

HostKeyAlgorithms ssh-ed25519

MACs hmac-sha2-512-etm@openssh.com,hmac-sha2-256-etm@openssh.com,umac-128-etm@openssh.com,hmac-sha2-512,hmac-sha2-256

KexAlgorithms curve25519-sha256,curve25519-sha256@libssh.org,diffie-hellman-group18-sha512,diffie-hellman-group16-sha512

#########
# OTHER #
#########

# Disable Protocol 1
# Legacy SSH protocol 1 is NOT secure
Protocol 2

# Compression
# Delayed option enables compression after authentication
Compression delayed

# Idle Log out time
# This will avoid unattended SSH Sessions
ClientAliveInterval 300
ClientAliveCountMax 0

# Strict Mode
# Using StrictModes enforces check on files in the home directory to ensure proper privileges and ownership is present
StrictModes yes

# Historically unsafe
IgnoreRhosts yes

ChallengeResponseAuthentication no

PermitEmptyPasswords no

# Disable root ssh login access
# This option still allows the use of su and sudo once in the terminal. It is recommended to use a normal user and then escalate privileges when required
PermitRootLogin no

# Fixes CVE-0216-0777
Host *
    UseRoaming no

X11Forwarding no

# Hash the known_hosts file to minimise usable information given to an attacker
HashKnownHosts Yes

# LogLevel VERBOSE logs user's key fingerprint on login. Needed to have a clear audit track of which key was using to log in.
# By default logs are retained until they consume up to 10% of the available disk space
LogLevel VERBOSE

# Disable ssh-agent forwarding to stop lateral movement
AllowAgentForwarding no

# disable reverse DNS lookups
UseDNS no

# allow a maximum of two sessions over a single TCP connection
MaxSessions 2

# set maximum authentication retries to prevent brute force attacks
MaxAuthTries 3
```

## Optional/Recommended Extra's

#### Disable Password Authentication
This option will disable password based logins meaning you will only be able to use SSH keys, this is the recommended setup, to learn more about setting up SSH Keys click here - [SSH Keys](ssh_keys.md)

```
PasswordAuthentication no
```

#### Disable Small Diffie-Hellman Key Sizes
The small Diffie-Hellman keysizes should be disabled in the moduli file before enabling diffie-hellman KexAlgorithms
```
awk '$5 >= 3071' /etc/ssh/moduli > /etc/ssh/moduli.safe
```
```
mv /etc/ssh/moduli.safe /etc/ssh/moduli
```

## Banner Example
The banner should be entered into the /etc/issue.net file

```
#################################################################
#                   _    _           _   _                      #
#                  / \  | | ___ _ __| |_| |                     #
#                 / _ \ | |/ _ \ '__| __| |                     #
#                / ___ \| |  __/ |  | |_|_|                     #
#               /_/   \_\_|\___|_|   \__(_)                     #
#                                                               #
#  You are entering into a secured area! Your IP, Login Time,   #
#   Username has been noted and has been sent to the network     #
#                       administrator!                          #
#   This service is restricted to authorized users only. All    #
#            activities on this system are logged.              #
#  Unauthorised access will be fully investigated and reported  #
#        to the appropriate law enforcement agencies.           #
#################################################################
```

This banner should be entered in the /etc/motd and will be shown after login

```
###############################################################
#                     SUPER SECURE SERVER                     #
###############################################################
#                   Welcome to Secureland                     #
#       All connections are monitored and recorded.           #
#  Disconnect IMMEDIATELY if you are not an authorised user!  #
###############################################################
```

After making changes restart the SSH daemon

```
sudo systemctl restart sshd
```