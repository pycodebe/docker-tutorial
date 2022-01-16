# Docker Tutorial

### Table of Content
- [SSH on Container to access it remotely](#SSH on Container to access it remotely)

<br />


## SSH on Container to access it remotely

For this demo I will be using the Debian image in docker. I am going to set up the SSH server, and then I will set up 
permissions for the user to access the container remotely. Then I will make an SSH connection from my Windows to the 
Debian machine

#### Local machine 
First you need to pull the debian images from docker Hub on your local machine and create a container using the 
command *docker run*.
```
docker pull debian
docker images
docker run -it --name debian-server -p 2200:22 -d debian:latest
docker ps
```

#### Docker container 
On the new container *debian-server* install *openssh-server* and nano. 
```
apt update
apt install openssh-server
apt install nano

## if you don't know the password of root, set a new password:
passwd
```
Edit the configuration file and enable root login over SSH. 
```
nano /etc/ssh/sshd_config
```
```
# Authentication:

#LoginGraceTime 2m
#PermitRootLogin prohibit-password
PermitRootLogin Yes
#StrictModes yes
#MaxAuthTries 6
#MaxSessions 10
```
Start the SSH server
```
service sshd start
```

#### Local machine

```
ssh root@localhost -p 2200
```
**Congratulation, you are connected to the remote Debian machine**