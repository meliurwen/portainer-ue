FROM golang:alpine AS builder-bin

ARG GOOS
ARG GOARCH
ARG GIT_TAG

COPY root_builder/remove_telemetry.patch /

RUN apk --update add git patch && \
    git clone --depth 1 --branch $GIT_TAG https://github.com/portainer/portainer.git && \
    cd portainer && \
    git apply /remove_telemetry.patch && \
    sh ./build/build_binary.sh $GOOS $GOARCH

FROM node:latest AS builder-client

ARG GIT_TAG

COPY root_builder /

RUN apt-get update && apt-get install git && \
    git clone --depth 1 --branch $GIT_TAG https://github.com/portainer/portainer.git && \
    cd portainer && \
    patch -p0 < /client_build_prod.patch && \
    git apply /remove_telemetry.patch && \
    cp -R /custom/* . && \
    yarn && \
    yarn build:client

FROM alpine:latest AS portainer

LABEL maintainer="Meliurwen <meliruwen@gmail.com>"

COPY --from=builder-bin /go/portainer/dist /
COPY --from=builder-client /portainer/dist /

WORKDIR /

EXPOSE 9000
EXPOSE 8000

ENTRYPOINT ["/portainer"]
