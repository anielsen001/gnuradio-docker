# Building Docker containers for arm

To cross-build for arm on x86_64 linux, install qemu packages
```bash
sudo apt-get install qemu binfmt-support qemu-user-static # Install the qemu packages
```

To choose an image, find out which architecture you have
```bash
cat /proc/cpuinfo | grep model
model name	: ARMv7 Processor rev 5 (v7l)
model name	: ARMv7 Processor rev 5 (v7l)
model name	: ARMv7 Processor rev 5 (v7l)
model name	: ARMv7 Processor rev 5 (v7l)
```

There may be an issue with `libseccomp` on the raspian os
see https://askubuntu.com/questions/1263284/apt-update-throws-signature-error-in-ubuntu-20-04-container-on-arm
Download the updated library here:
```bash
wget http://ftp.us.debian.org/debian/pool/main/libs/libseccomp/libseccomp2_2.5.4-1+b2_armhf.deb
```
and install

```bash
sudo dpkg -i libseccomp2_2.5.4-1+b2_armhf.deb
```

# Raspberry pi docker set up

## Install Docker

Download the installation script and run:
```bash
curl -sSL https://get.docker.com -o get_docker.sh
sudo bash get_docker.sh
```

Add user pi to the docker user group
```bash
sudo usermod -aG docker pi
```

Reboot and log back into make sure the daemon starts
```bash
sudo reboot
```

Test the docker install
```bash
docker run hello-world
```

## Install docker-compose

Basic requirements:
```bash
sudo apt install libffi-dev libssl-dev
sudo apt install python3-dev
sudo apt-get install -y python3 python3-pip
```

Install rust:
```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
```

Install docker-compose, this step will take a while
```bash
pip3 install docker-compose
```
