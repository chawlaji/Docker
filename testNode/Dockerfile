# use this empty Dockerfile to build your assignment

# This dir contains a Node.js app, you need to get it running in a container
# - use the 'node' official image, with the alpine 6.x branch
FROM node:6-alpine
# - this app listens on port 3000, but the container should launch on port 80
  #  so it will respond to http://localhost:80 on your computer
  EXPOSE 3000
# - then it should use alpine package manager to install tini: 'apk add --update tini'
RUN apk add --update tini
# - then it should create directory /usr/src/app for app files with 'mkdir -p /usr/src/app'
RUN mkdir -p /usr/src/app
# - Node uses a "package manager", so it needs to copy in package.json file
WORKDIR /usr/src/app
COPY package.json package.json
# - then it needs to run 'npm install' to install dependencies from that file

# - to keep it clean and small, run 'npm cache clean --force' after above
RUN npm install && npm cache clean --force
# - then it needs to copy in all files from current directory
COPY . .
# - then it needs to start container with command 'tini -- node ./bin/www'
# - in the end you should be using FROM, RUN, WORKDIR, COPY, EXPOSE, and CMD commands
CMD ["tini","--","node","./bin/www"]
# Bonus Extra Credit
# this will not have you setting up a complete image useful for local develement, test, and prod
# it's just meant to get you started with basic Dockerfile concepts and not focus too much on

