#Specify the base image
FROM node:alpine

#Setting the working directory
WORKDIR /app

#COPY file package.json to container file system
COPY ./package.json ./

#Install dependencies
RUN npm install

COPY . .

#Default command
CMD ["npm", "run", "build"]

#copy build folder to NGINX

FROM nginx
EXPOSE 3000
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
