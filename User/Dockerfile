FROM node:20-alpine AS deps

WORKDIR /app

COPY . /app

EXPOSE 3001:3001

RUN npm install

CMD npm run dev