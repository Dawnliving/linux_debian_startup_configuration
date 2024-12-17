# Archive versions JDK configuration

Using apt repository to manage software

(Applies to other software as well)



(In Ubuntu official apt repository, it doesn't archive previous versions software so fast, hence can install openjdk8 without any configuration)

(But In debian or other linux archive previous versions as system update, can not install archive version software by using its official apt repository directly.)

(The third party package management can be considered as well, such as slackware)



In this case, I choose to add adoptium repository.

```shell
sudo echo "deb [arch=amd64] https://some.repository.url focal main" | sudo tee /etc/apt/sources.list.d/adoptium.list > /dev/null
```

```shell
sudo apt install -y wget apt-transport-https gpg
```

```shell
wget -qO - https://packages.adoptium.net/artifactory/api/gpg/key/public | gpg --dearmor | tee /etc/apt/trusted.gpg.d/adoptium.gpg > /dev/null
```

```shell
sudo echo "deb https://packages.adoptium.net/artifactory/deb $(awk -F= '/^VERSION_CODENAME/{print$2}' /etc/os-release) main" | sudo tee /etc/apt/sources.list.d/adoptium.list
```

```shell
apt update # update if you haven't already
```

