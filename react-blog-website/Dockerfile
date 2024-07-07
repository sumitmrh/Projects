FROM node:14

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

ENV NODE_OPTION=--openssl-legeacy-provider

EXPOSE 3000

CMD ["npm","run","build","start"]
