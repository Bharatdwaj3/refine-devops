FROM node:22-alpine AS deps

WORKDIR /app

COPY . /app

EXPOSE 3002:3002

RUN npm install

CMD npm run dev