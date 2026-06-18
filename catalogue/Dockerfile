FROM node:22.22-alpine3.24 AS build
WORKDIR /opt/server
COPY package.json .
COPY *.js .

# this may add extra cache memory we can use multi satge build 
RUN npm install 

FROM node:22.22-alpine3.24
RUN addgroup -S roboshop && adduser -S roboshop -G roboshop
WORKDIR /opt/server
USER roboshop
COPY --from=build /opt/server /opt/server
ENV MONGO=true\
    MONGO_URL="mongodb://mongodb:27017/catalogue"
RUN chown -R roboshop:roboshop /op/server    
CMD ["node","server.js"]    
