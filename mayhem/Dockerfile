# Build Stage:

FROM --platform=linux/amd64 ubuntu:20.04 as builder

## Install build dependencies.
RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get install -y libncursesw5-dev autotools-dev autoconf build-essential 

## Add Source Code
ADD . /
WORKDIR /

## Build Step
RUN ./autogen.sh && ./configure && make

# Package Stage
FROM --platform=linux/amd64 ubuntu:20.04

COPY --from=builder /htop /