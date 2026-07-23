
#!/usr/bin/env bash (for the script)

##### Upgrade Linux OS after fresh install. #####

sudo apt update && sudo apt upgrade -y

###### Install Guest Agent #####
sudo apt-get install qemu-guest-agent

###### Install NVIDIA Drivers ######
sudo ubuntu-drivers install
sudo apt install nvtop

###### Docker install ######
sudo apt-get update
sudo apt-get install -y ca-certificates curl
sudo install -m 0755 -d /etc/apt/keyrings
sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc
sudo chmod a+r /etc/apt/keyrings/docker.asc
sudo tee /etc/apt/sources.list.d/docker.sources <<EOF
Types: deb
URIs: https://download.docker.com/linux/ubuntu
Suites: $(. /etc/os-release && echo "${UBUNTU_CODENAME:-$VERSION_CODENAME}")
Components: stable
Signed-By: /etc/apt/keyrings/docker.asc
EOF
sudo apt update
sudo apt install docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

#### check docker status #####
sudo systemctl status docker
