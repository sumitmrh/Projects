FROM node:16-alpine

WORKDIR /app

COPY package.json package-lock.json ./

RUN npm install

RUN npm install -g @angular/cli@15.0.4

COPY . /app/

EXPOSE 4200

CMD ["ng", "serve", "--host", "0.0.0.0"]
