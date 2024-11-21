ARG CLOUDHARNESS_FRONTEND_BUILD

FROM $CLOUDHARNESS_FRONTEND_BUILD as builder
WORKDIR /usr/local/app

# Copy the dependencies directory
COPY dependencies/neuroglancer .

# Install dependencies
RUN npm install

# Build the application
RUN npm run build

FROM nginx:1.25-alpine

WORKDIR /usr/share/nginx/html

RUN rm -rf ./*
COPY --from=builder /usr/local/app/dist/client .

CMD ["nginx", "-g", "daemon off;"]
