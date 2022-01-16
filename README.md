## Docker tutorial

This website is a collection of tutorials based on the issues that I have had to deal with during my projects

### Table of Content
- [SSH on Container to access it remotely](# SSH on Container to access it remotely)

<br />

### SSH on Container to access it remotely

For this demo I will be using the Debian image in docker. I am going to set up the SSH server, and then I will set up 
permissions for the user to access the container remotely. Then I will make a SSH connection from my Windows to the 
Debian machine



#### Pull the Debian image from [docker Hub](https://hub.docker.com/_/debian)
```markdown
docker pull debian
```


#### Check if the Debian image has been downloaded
```markdown
docker image debian
```

#### Create the debian-server container
```markdown
docker run -it --name debian-server -p 2200:22 -d debian:latest
```

