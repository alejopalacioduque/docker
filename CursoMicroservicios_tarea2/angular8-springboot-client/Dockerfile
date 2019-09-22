# FROM node:12.2.0-alpine as builder
# RUN mkdir -p /usr/src/app
# WORKDIR /usr/src/app
# COPY package.json /usr/src/app
# RUN npm cache verify
# RUN npm install
# COPY . /usr/src/app
# EXPOSE 4200
# CMD ["npm","start"]

FROM node:12.2.0-alpine as builder
# set working directory
WORKDIR /app
# add `/app/node_modules/.bin` to $PATH
ENV PATH /app/node_modules/.bin:$PATH
# install and cache app dependencies
COPY package.json /app/package.json
RUN npm install && npm install -g @angular/cli && npm cache verify
# add app
COPY . /app
# start app
CMD ng serve --host 0.0.0.0 --port 4200 --public-host http://localhost:4200

