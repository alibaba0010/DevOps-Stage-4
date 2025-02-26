FROM node:18-alpine

# ARG APP_DIR
WORKDIR /usr/src/todos-api
COPY package*.json ./

RUN npm install

COPY ./ ./

# RUN npm run dev:auth
CMD [ "npm", "run", "start" ]

EXPOSE 8082
