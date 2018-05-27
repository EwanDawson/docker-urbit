FROM debian:buster
MAINTAINER Ewan Dawson <ewan.dawson@lazygun.net>

RUN apt-get update \
    && apt-get install -y autoconf automake cmake exuberant-ctags g++ git \
    libcurl4-gnutls-dev libgmp3-dev libncurses5-dev libsigsegv-dev libssl-dev \
    libtool make meson openssl pkg-config python ragel re2c zlib1g-dev

RUN git clone https://github.com/urbit/urbit

RUN cd urbit && ./scripts/bootstrap

RUN cd urbit && ./scripts/build

RUN cd urbit && ninja -C ./build/ meson-install

WORKDIR /urbit
EXPOSE 8443
ENTRYPOINT ["urbit"]
