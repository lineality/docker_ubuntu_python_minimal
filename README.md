# docker_ubuntu_python_minimal


# Overview
If you are setting up docker on ubuntu linux to run a python script, here is sample minimal code. Follow each step and run each command in your terminal. Instructions that start with "$" are likely terminal commands. Other instructions will be text to copy into files.


## New Project Folder
It is recommended that you create a project-folder and then do your work in that folder("directory"). Run this line of code to create a project folder and then make that folder the "current working directory" where your terminal opera"my_project_folder" is arbitrary, you can name your project anything you like.
```
$ mkdir my_project_folder; cd my_project_folder
```

## Remove Old Docker Files 
```
$ sudo docker system prune
```

## First Setup Bash Script
```
$ touch app.py; touch Dockerfile; touch requirements.txt; touch readme.md
```

## readme.md / readme.txt 
Having a readme or instructions file is helpful for documentation and clear communication. You can put the contents of this guide into that readme file. 
```
# Instructions and Guide
```

## requirements.txt
Add this text to your file. This specific minimal project has no required text, no required packages, but some docker applications require a 'requirements.txt' file even if that file is blank. (e.g. AWS-lambda-function docker-containers)
```
# list of python requirements
```

# Dockerfile
Add this text to your file. 
```
# Get docker base image
FROM ubuntu:18.04

# Update ubuntu linux software and packages
RUN apt-get update -y

# Install and update pip and python-dev 
RUN apt-get install -y python3-pip python3-dev

# Import requirements.txt into docker
COPY ./requirements.txt /requirements.txt

# Set working directory
WORKDIR /

# Install python requirements
RUN pip3 install -r requirements.txt

# Copy all files in project directory into docker
COPY . /

# Specify the executable to run
ENTRYPOINT [ "python3" ]

# The function of this docker is to run the app.py
CMD [ "app.py" ]
```

# app.py
Add this text to your file. 
```
print( "Hello, World." )
```

## Build your Docker image
Add this text to your file. The period "." is not a typo:
```
sudo docker build -t abc .
```

#### Successful builds output these lines at end:
```
Successfully built ############
Successfully tagged ###:latest
```

## Run your Docker container
```
$ sudo docker run -p 9000:8080 abc:latest
```

#### Successful run should output something like this: 
```
Hello, World.
```

## Remove Old Files 
```
$ sudo docker system prune -y
```

## Sources and Resources
- use ubuntu, install docker
- https://docs.docker.com/engine/install/ubuntu/
- https://www.educba.com/docker-entrypoint/
- https://linuxhint.com/docker-entrypoint-beginner-guide/ 
