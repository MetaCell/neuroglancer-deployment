FROM node:20-alpine as builder
RUN apk update && \
    apk add git && \
    rm /var/cache/apk/*
ARG NG_BRANCH_NAME=develop
ARG FORCE_CLONE=0
ENV BRANCH_NAME=$NG_BRANCH_NAME
RUN git clone -b ${NG_BRANCH_NAME} https://github.com/MetaCell/neuroglancer.git /usr/local/app
WORKDIR /usr/local/app
RUN npm install
RUN npm run build

FROM nginx:1.25-alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=builder /usr/local/app/dist/min .
CMD ["nginx", "-g", "daemon off;"]
