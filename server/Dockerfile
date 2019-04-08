FROM node:10-alpine
RUN apk add --update tini
# RUN apk add --update tini make gcc g++ python
ENTRYPOINT ["/sbin/tini", "--"]

WORKDIR /app

ENV YARN_VERSION 1.15.2
ENV NODE_ENV=production
COPY ./package.json ./yarn.lock /app/
RUN yarn install
COPY . /app/
CMD [ "npm", "start"]