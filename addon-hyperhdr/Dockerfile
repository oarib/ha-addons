# ----------------------
# Updated Dockerfile
# ----------------------

ARG BASE_IMAGE=ubuntu:22.04
FROM ${BASE_IMAGE}

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

# Install dependencies
RUN apt-get update && apt-get install -y --no-install-recommends \
    git cmake build-essential \
    qtbase5-dev qttools5-dev qttools5-dev-tools \
    libqt5serialport5-dev libqt5svg5-dev \
    libusb-1.0-0-dev libturbojpeg-dev \
    libavcodec-dev libavformat-dev libswscale-dev \
    libudev-dev libasound2-dev \
    libglvnd-dev libv4l-dev \
    pkg-config tzdata \
    libssl-dev flatbuffers-compiler libflatbuffers-dev libzstd-dev \
    && rm -rf /var/lib/apt/lists/*

COPY hyperhdr-source /opt/hyperhdr
WORKDIR /opt/hyperhdr

RUN mkdir build && cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr .. && \
    make -j$(nproc) && \
    make install

CMD ["hyperhdr"]
