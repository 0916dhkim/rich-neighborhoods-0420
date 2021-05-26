FROM node:12-alpine AS builder
ARG REACT_APP_API_SERVER_URL
ENV REACT_APP_API_SERVER_URL $REACT_APP_API_SERVER_URL
WORKDIR /app
COPY . .
RUN yarn install --production
RUN yarn build

FROM nginx
COPY ./nginx.conf /etc/nginx/templates/default.conf.template
COPY --from=builder /app/build /usr/share/nginx/html

