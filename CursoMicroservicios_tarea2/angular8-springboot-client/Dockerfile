FROM node:12.2.0-alpine as builder
# set working directory
WORKDIR /app
# Env variable app path
ENV PATH /app/node_modules/.bin:$PATH
# install and cache app dependencies
COPY package.json /app/package.json
RUN npm install && npm install -g @angular/cli && npm cache verify
# add app
COPY . /app
# start app
CMD ng serve --host 0.0.0.0 --port 4200 --public-host http://localhost:4200

