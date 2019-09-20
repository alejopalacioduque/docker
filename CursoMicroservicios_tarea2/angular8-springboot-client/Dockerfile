FROM node:12.2.0-alpine as builder

#WORKDIR /usr/src/app

#COPY package*.json ./

#RUN npm install

#COPY . .

#RUN npm run build

#FROM nginx:1-alpine
#COPY --from=builder /usr/src/app/dist/ /usr/share/nginx/html
#EXPOSE 80

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
CMD ng serve --host 0.0.0.0
