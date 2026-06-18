FROM node:22.22-alpine3.24
WORKDIR /opt/server
COPY package.json .
COPY *.js .
RUN npm install 
ENV MONGO=true\
    MONGO_URL="mongodb://mongodb:27017/catalogue"
CMD ["node","server.js"]    
