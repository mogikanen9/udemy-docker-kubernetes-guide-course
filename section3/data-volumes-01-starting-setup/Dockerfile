FROM node:14

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . .

# 'app' is WORKDIR and 'feedback' is a folder from serve.js code
# VOLUME [ "/app/feedback" ]

ENV PORT 8080

EXPOSE 8080

CMD ["node","server.js"]
