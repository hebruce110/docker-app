FROM node:10.16.0-alpine

LABEL version="1.0"
LABEL description="node10.16.0"
LABEL maintainer="bruce<heyuan110@gmail.com>" 
LABEL dockerhub="https://hub.docker.com/u/heyuan110"
LABEL github="https://github.com/heyuan110/docker-app"

COPY ./.npmrc /root/.npmrc

# add extra tools and gulp 
RUN apk add --no-cache make gcc g++ python && \
    npm install --global gulp



