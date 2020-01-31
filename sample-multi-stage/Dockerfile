FROM node:10-slim as prod
ENV NODE_ENV=production

EXPOSE 3000

COPY package*.json ./

RUN npm install --only=prod && npm cache clean --force

COPY . .

CMD ["node", "./bin/www"]

FROM prod as dev
ENV NODE_ENV=development

# Don't need cache clean. Fast build is more important than space on local machine
RUN npm install --only=dev 

# CMD ["npm", "run", "dev", "app.js"] 

# remember using npn in docker is not optimal.
# do this instead
# see package.json to get the arguments
CMD ["nodemon",  "./bin/www", "--inspect=0.0.0.0:9229"]

FROM dev as test
ENV NODE_ENV=development

CMD ["npm", "test"]
