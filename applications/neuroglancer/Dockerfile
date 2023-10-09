FROM node:20 as build

RUN git clone https://github.com/metacell/neuroglancer

# BUILD STEPS


FROM nginx

COPY --from build ...