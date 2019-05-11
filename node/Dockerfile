# Set the base image to Ubuntu
FROM    ubuntu:14.04

# File Author / Maintainer
MAINTAINER Anand Mani Sankar

# Install Node.js and other dependencies
RUN apt-get update && \
  apt-get -y install curl && \
  curl -sL https://deb.nodesource.com/setup_dev | bash - && \
  apt-get -y install python build-essential nodejs ssh

# Install nodemon
RUN npm install -g nodemon

# Provides cached layer for node_modules
ADD package.json /tmp/package.json
RUN cd /tmp && npm install
RUN mkdir -p /src && cp -a /tmp/node_modules /src/

# Define working directory
WORKDIR /src
ADD . /src

# Expose port
EXPOSE  8888

# Run app using nodemon
CMD ["nodemon", "/src/index.js"]
