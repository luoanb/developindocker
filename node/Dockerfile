FROM node:lts-alpine
RUN echo "http://mirrors.aliyun.com/alpine/edge/main/" > /etc/apk/repositories \
    && echo "http://mirrors.aliyun.com/alpine/edge/community/" >> /etc/apk/repositories \
    && apk update \
    && apk add --no-cache --update git 
# ENV NODE_ENV=production
# RUN apk update
# RUN apk add git
WORKDIR /usr/src/app
RUN npm install -g pnpm nrm open@8.4.2 --save --registry=https://registry.npmmirror.com \
    && nrm use tencent 
# COPY . .
EXPOSE 80
RUN chown -R node /usr/src/app \
    && chown -R node /usr/local/lib \
    && chown -R node /usr/local/bin
USER node
RUN pnpm config set store-dir ~/.pnpm-store
CMD "/bin/sh"
