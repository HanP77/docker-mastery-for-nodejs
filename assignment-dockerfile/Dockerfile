# fill in the blanks to dockerize this node app
FROM node:10.15-alpine

EXPOSE 3000

WORKDIR /usr/src/app

COPY package*.json ./  

RUN npm install && npm cache clean --force

COPY . .

CMD ["node", "app.js"]
