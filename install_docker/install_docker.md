# Install Docker
## Description
This tutorial lists the steps to install and setup docker in your Ubuntu VM.

## Pre-requisites
- [Setting up VM Environment](../virtual_machine_setup/tutorial.md)

## Steps
1. Uninstall older versions of docker, uninstall them:
    ```bash
    sudo apt remove docker docker-engine docker.io containerd runc
    ```
2. Update the apt package index and install packages to allow apt to use a repository over HTTPS:
    ```bash
    sudo apt update
    sudo apt install -y apt-transport-https ca-certificates curl gnupg lsb-release
    ```
3. Add Docker's official GPG key:
    ```bash
    curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo gpg --dearmor -o /usr/share/keyrings/docker-archive-keyring.gpg
    ```
4. Use the following command to set up the stable repository:
    ```bash
    echo \
    "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyring.gpg] https://download.docker.com/linux/ubuntu \
    $(lsb_release -cs) stable" | sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
    ```
5. Update the apt package index, and install the latest version of Docker Engine and containerd:
    ```bash
    sudo apt update
    sudo apt install -y docker-ce docker-ce-cli containerd.io
    ```
6. Verify that Docker Engine is installed correctly by running the hello-world image.
    ```bash
    sudo docker run hello-world
    ```

### Manage Docker as a non-root user
The Docker daemon binds to a Unix socket instead of a TCP port. By default that Unix socket is owned by the user root and other users can only access it using sudo. The Docker daemon always runs as the root user. Some Xilinx scripts that launch docker containers cannot run as root user, so you need to enable docker to run without the sudo command. That can be done by creating a Unix group called `docker` and add users to it. When the Docker daemon starts, it creates a Unix socket accessible by members of the docker group. Follow the steps below to create the docker group and add your user:

1. Create the docker group:
    ```bash
    sudo groupadd docker
    ```
2. Add your user to the docker group.
    ```bash
    sudo usermod -aG docker $USER
    ```
    restart the virtual machine for changes to take effect.
3. Verify that you can run docker commands without sudo.
    ```bash
    docker run hello-world
    ```
