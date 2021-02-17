FROM node:12 as build-step
RUN mkdir -p /app
WORKDIR /app
COPY package.json /app
COPY . /app
RUN npm install 
RUN npm run build 

FROM nginx:latest
RUN rm /etc/nginx/conf.d/default.conf
RUN rm -f /etc/nginx/conf.d/examplessl.conf
COPY --from=build-step /app/dist/angular-simple /var/www/virtual/
COPY ./nginx-conf /etc/nginx

