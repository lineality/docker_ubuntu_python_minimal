# docker_ubuntu_python_minimal

## Remove Old Files 
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

## Requirements.txt
```
# this minimal starter project has no requirements
```

# Dockerfile
```
# get docker base image
FROM ubuntu:18.04

# update ubuntu linux software and packages
RUN apt-get update -y

# install and update pip and python-dev 
RUN apt-get install -y python3-pip python3-dev

# import requirements.txt into docker
COPY ./requirements.txt /requirements.txt

# set working directory
WORKDIR /

# install python requirements
RUN pip3 install -r requirements.txt

# ??
COPY . /

# specify the executable to run
ENTRYPOINT [ "python3" ]

# the function of this docker is to run the app.py
CMD [ "app.py" ]
```

# app.py
```
print( "Hello, World." )
```

## Build your Docker image
The period "." is not a typo:
```
sudo docker build -t abc .
```

#### Successful builds outputs these lines at end:
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
