# Set the base image to Ubuntu
FROM ubuntu:14.04

# File Author / Maintainer
MAINTAINER Anand Mani Sankar

# Install Node.js and other dependencies
RUN apt-get update && \
  apt-get -y install curl && \
  curl -sL https://deb.nodesource.com/setup_8.x | bash - && \
  apt-get -y install python build-essential nodejs ssh

# Install nodemon
RUN npm install -g nodemon

# Provides cached layer for node_modules
COPY package.json /tmp/package.json
WORKDIR /tmp
RUN npm install
RUN mkdir -p /src && cp -a /tmp/node_modules /src/

# Define working directory
WORKDIR /src
COPY . /src

# Expose port
EXPOSE  8888

# Run app using nodemon
CMD ["nodemon", "/src/index.js"]
