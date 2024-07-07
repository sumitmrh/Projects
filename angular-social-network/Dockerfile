FROM node:16-alpine

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install

RUN npm install -g @angular/cli@14.0.2

COPY . /app/

CMD ["ng", "serve", "--host", "0.0.0.0"]
