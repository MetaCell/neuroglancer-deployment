FROM node:20-alpine as builder
RUN git clone https://github.com/google/neuroglancer.git /usr/local/app
WORKDIR /usr/local/app
RUN npm install
RUN npm run build

FROM nginx:1.25-alpine
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*
COPY --from=builder /usr/local/app/dist .
CMD ["nginx", "-g", "daemon off;"]