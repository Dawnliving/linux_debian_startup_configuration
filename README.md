# Linux(Debian) Startup Configuration

System: Debian12.5

## Terminal Font Configuration

```shell
sudo dpkg-reconfigure locales
```

Then choose en-US.UTF-8 to allow terminal support the UTF-8 format Font.

## Add sudoers

```shell
su -
```

switch to root, enter root password

```shell
nano /etc/sudoers
```

add the sudoers

```config
username  ALL=(ALL:ALL) ALL
```

replace 'username' with user you create

## (Optional) Generate Key Pairs

In client ssh (window can use powershell or cmd)

```shell
ssh-keygen -t RSA -b 4096 -P '' -f "/PATH/TO/FILENAME"
```

It will generate a keypairs, default file name are id_rsa and id_rsa.pub.

Notice:

id_rsa is the defalt file name generated, and lots of software can automatically use id_rsa keypair to connect ssh, so if keypairs are used to reduce frequency of entering password, please keep keypair filename as default or "id_rsa". For example, hadoop, git access github.com via ssh.

## Configure SSH Key Pairs(can do with root and other users)

If user doesn't have ssh key pair, make directory first

```ssh
mkdir ~/.ssh
```

```shell
touch ~/.ssh/authorized_keys
```

```shell
nano ~/.ssh/authorized_keys
```

Then add the public part of ssh key pairs (id_rsa.pub) into authorized_keys and save. Next time can use private part of designated key pairs (id_rsa) to login ssh. 

To distinguish different protocol,  if use **openssh** protocol to access ssh, keypair private file will have no suffix or .pem .key suffix, if use putty protocol to access ssh, keypair private file will have .ppk suffix.

## Add apt repository

```shell
sudo nano /etc/apt/source.list
```

### source.list

Debian official apt repository( can change base on demand and network condition)

```list
deb https://deb.debian.org/debian bookworm main non-free-firmware non-free contrib
deb-src https://deb.debian.org/debian bookworm main non-free-firmware non-free contrib

deb https://security.debian.org/debian-security bookworm-security main non-free-firmware non-free contrib
deb-src https://security.debian.org/debian-security bookworm-security main non-free-firmware non-free contrib

deb https://deb.debian.org/debian bookworm-updates main non-free-firmware non-free contrib
deb-src https://deb.debian.org/debian bookworm-updates main non-free-firmware non-free contrib
```

```shell
sudo apt update
```

## Other basic software installation

### MySQL

[MySQL installation and configuration](./MySQL_Installation.md)

### Archive Version JDK(applies to other software as well)

through adding third party apt repository

[Archive Version JDK](./Archive_versions_JDK_configuration.md)
