# Get docker image
FROM node:6-alpine

# Update packages and install tini
RUN apk update && apk add --no-cache tini

# Add info or metadata to the image
LABEL version=1.0
LABEL description="NodeJs image"
MAINTAINER  "Alejandropalacio <alejopalacioduque@gmail.com>"

# Expose and map ports
EXPOSE 3000

# create folder to store app files
RUN mkdir -p /usr/scr/app

# Define work app directory
WORKDIR /usr/src/app

# Copy the package.json file
COPY package.json .

#Install app node pakages
RUN npm install && npm cache clean --force

# Copy app files
COPY . .

# Define Entrypoint
ENTRYPOINT [ "/sbin/tini", "--", "node", "./bin/www" ]
