FROM node:14

WORKDIR /app

COPY package.json /app

RUN npm install

COPY . .

# 'app' is WORKDIR and 'feedback' is a folder from serve.js code
# VOLUME [ "/app/feedback" ]

ARG DEFAULT_PORT=8080

ENV PORT ${DEFAULT_PORT}

EXPOSE ${PORT}

CMD ["node","server.js"]
