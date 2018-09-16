FROM node:8-slim as todofront

RUN mkdir -p /todofront
WORKDIR /todofront

COPY ./todofront/package.json .
COPY ./todofront/yarn.lock .

RUN yarn install

ADD ./todofront/ .

RUN yarn build


FROM nginx:1.15

WORKDIR /

# Copy todofront dist to nginx
COPY --from=todofront /todofront/dist /usr/share/nginx/html/dist

# Copy configuration files to the container
COPY ./nginx/conf.d/local.conf /etc/nginx/conf.d/default.conf
