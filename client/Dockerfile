FROM node:12-alpine AS builder
ARG REACT_APP_API_SERVER_URL
ENV REACT_APP_API_SERVER_URL $REACT_APP_API_SERVER_URL
WORKDIR /app
COPY . .
RUN yarn install --production
RUN yarn build

FROM node:12-alpine
WORKDIR /public
COPY --from=builder /app/build /public
RUN yarn global add serve

CMD serve -s /public

