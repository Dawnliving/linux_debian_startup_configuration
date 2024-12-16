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



