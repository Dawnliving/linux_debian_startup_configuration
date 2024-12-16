# Archive versions JDK configuration

(Applies to other software as well)

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

