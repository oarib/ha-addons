FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

RUN apt-get update && apt-get install -y \
    git cmake build-essential qtbase5-dev libqt5serialport5-dev \
    libusb-1.0-0-dev libturbojpeg0-dev libavcodec-dev libavformat-dev \
    libswscale-dev libqt5svg5-dev qttools5-dev-tools qttools5-dev \
    libudev-dev pkg-config tzdata && \
    rm -rf /var/lib/apt/lists/*

# Copier les sources depuis le workflow GitHub Actions
COPY hyperhdr-source /opt/hyperhdr

WORKDIR /opt/hyperhdr

# Debug : afficher le contenu
RUN ls -l /opt/hyperhdr && cat CMakeLists.txt || echo "CMakeLists.txt missing"

RUN mkdir build && cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release .. && \
    make -j$(nproc) && make install

CMD ["hyperhdr"]
