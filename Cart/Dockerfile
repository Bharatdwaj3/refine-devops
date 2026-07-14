FROM node:22-alpine AS deps

WORKDIR /app

COPY . /app

EXPOSE 3003:3003

RUN npm install

CMD npm run dev