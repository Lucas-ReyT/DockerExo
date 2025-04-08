FROM node:latest
 
RUN npm install -g npm@11.1.0
 
WORKDIR /app
 
COPY package*.json .
 
RUN npm i
 
COPY . .
 
CMD ["node", "server.js"]
 
 
 