# build react project

FROM node:14 as base

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

RUN npm run build

# create distro

FROM registry.access.redhat.com/rhscl/nginx-112-rhel7

USER 0

RUN rm -rf /usr/share/nginx/html/* && \
    rm -f /etc/opt/rh/rh-nginx112/nginx/nginx.conf

COPY nginx.conf /etc/opt/rh/rh-nginx112/nginx/

RUN chgrp 0 /etc/opt/rh/rh-nginx112/nginx/nginx.conf && \
    chmod g=u+x /etc/opt/rh/rh-nginx112/nginx/nginx.conf

COPY --from=base /app/build/ /opt/app-root/src

EXPOSE 8080

CMD ["/bin/sh",  "-c",  "exec nginx -g 'daemon off;'"]