# LithOS

[![Build LithOS Image](https://github.com/TechnocultureResearch/LithOS/actions/workflows/buildImage.yml/badge.svg?branch=kirkstone)](https://github.com/TechnocultureResearch/LithOS/actions/workflows/buildImage.yml)

## Pre-requisites

```sh
sudo apt install python3 python3-pip
```
```sh
sudo pip3 install distro jsonschema kconfiglib PyYAML
```
- Docker

```sh
sudo apt-get update
```
```sh
 sudo apt-get install     ca-certificates     curl     gnupg     lsb-release
```
```sh
sudo mkdir -p /etc/apt/keyrings
```
```sh
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
```

```sh
echo   "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/ubuntu \
  $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```
```sh
sudo apt-get update
```
```sh
sudo apt-get install docker-ce docker-ce-cli containerd.io docker-compose-plugin
```

```sh
apt-cache madison docker-ce
```
- Install a specific version  using version string from second column 
- `
sudo apt-get install docker-ce=<VERSION_STRING> docker-ce-cli=<VERSION_STRING> containerd.io docker-compose-plugin
`
```sh
sudo apt-get install docker-ce= 5:20.10.17~3-0~ubuntu-focal docker-ce-cli= 5:20.10.17~3-0~ubuntu-focal containerd.io docker-compose-plugin
```
- Check if docker installation successfull
```sh
sudo docker run hello-world
```
```sh
sudo groupadd docker
```
```sh
sudo usermod -aG docker $USER
```
```sh
newgrp docker
```
- Verify if we can run docker command without sudo
```sh
docker run hello-world
```
![Screenshot from 2022-08-31 15-46-22](https://user-images.githubusercontent.com/86110190/187656098-657ea6b4-bd9f-4611-8167-0d01164b5f55.png)

```sh
sudo systemctl enable docker.service
```
```sh
sudo systemctl enable containerd.service
```
```sh
echo $USER
```
```sh
sudo usermod -aG docker $USER
```
```sh
sudo systemctl restart docker
```
```sh
docker ps
```

- Cargo
```sh
apt-get -y install cargo
```
```sh
cargo install cargo-bitbake
```
```sh
cargo install cargo-bitbake --force
````
```sh
sudo apt-get install build-essential gcc bv bison flex libssl-dev libncurses5-dev libelf-dev
```
```sh
sudo apt-get install build-essential libncurses5-dev
```

### Clone kas

```sh
git clone https://github.com/siemens/kas
```

This repository contains the script that we will be using to build images, sdk and access the yocto development environment. The key script we will be using is `kas-container`.

## Build Instructions

### Build Image

Use this command from LithOS repo to build the image.

```sh
$PATH_TO_KAS_DIR/kas-container build kirkstone.yaml
```

### Access development environment shell

```sh
$PATH_TO_KAS_DIR/kas-container shell kirkstone.yaml
```

- Build file can be found at
- `/build/tmp/deploy/images/raspberrypi4`

> Refer the [documentation](https://kas.readthedocs.io/en/latest/) for more info.
> This approach comes from [this blog](https://embeddeduse.com/2022/06/24/setting-up-yocto-projects-with-kas/) by [Embedded Use](https://embeddeduse.com).

---

> ⚠️ [`OTA Procedure`](./OTA.md)
