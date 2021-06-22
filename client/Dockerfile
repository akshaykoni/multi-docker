FROM node:alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
RUN npm run build    //this is going to build the source code in one single file 

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf 
#we are copying the configuration file for nginx to th default location of config file

COPY --from=builder /app/build /usr/share/nginx/html
#we are using that single build file and we are telling it to copy in this locaton for the hosting