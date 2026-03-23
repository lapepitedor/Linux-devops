# Installing Docker on Ubuntu (Step-by-StepGuide)

Docker is a containerization platform that allows you to package applications and theirdependencies into isolated environments called
containers. This guide will show youhow to install and configure Docker on Ubuntu.

## 1.Update your System

Before installing Docker, update your package list to ensure you are installing the latestversions of dependencies.

Open the terminal and run:


```bash
sudo apt update && sudo apt upgrade -y
```

## 2. Install Required Dependencies

```bash
sudo apt install apt-transport-https ca-certificates curl software-prope
```

##  3. Add Docker’s Official GPG Key

```bash
curl -fsSL https://download.docker.com/linux/ubuntu/gpg| sudo gpg --dea
```

## 4. Add Docker Repository

```bash
echo "deb [arch=amd64 signed-by=/usr/share/keyrings/docker-archive-keyri
```

## 5. Install Docker

```bash
sudo apt updatesudo apt install docker-ce docker-ce-cli containerd.io -y
```

## 6. Verify Docker Installation

To check if docker is  installed correctly, run:

```bash
docker --version
```
you should see output similar to:

```bash
Docker version 24.0.5, build ced0996
```

## 7. Start and Enable Docker

To start Docker and enable it to launch on boot, run:

```bash
sudo systemctl start docker
sudo systemctl enable docker
```
Verify if Docker is running:

```bash
sudo systemctl status docker
```

If running, you will see "active (running)" in green.

Test Docker:

```bash
docker run hello-world
```
You will get error:

```bash
docker: permission denied while trying to connect to the Docker daemon 
```

## 8. Run Docker Without sudo (Optional but Recommended)

By default, Docker commands require sudo. To run Docker without sudo, add your userto the docker group:

```bash
sudo usermod -aG docker $USER
```

Now, log out and log back in, or run:

```bash
newgrp docker
```

Try running Docker without sudo:

```bash
docker run hello-world
```
If successful, you will see:

```bash
Hello from Docker!This message shows that your installation appears to be working correctly.
```

## 9. Test Docker Installation

Run the following command to check if Docker is working:

```bash
docker run hello-world
```

This downloads a small test container and runs it.

























