# Stage 1: Build HyperHDR
FROM ubuntu:22.04 AS builder

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

RUN apt-get update && apt-get install -y --no-install-recommends \
    git cmake build-essential \
    qtbase5-dev qttools5-dev qttools5-dev-tools \
    libqt5serialport5-dev libqt5svg5-dev \
    libusb-1.0-0-dev libturbojpeg0-dev \
    libavcodec-dev libavformat-dev libswscale-dev \
    libudev-dev libasound2-dev \
    libglvnd-dev libv4l-dev \
    pkg-config tzdata \
    libssl-dev flatbuffers-compiler libflatbuffers-dev libzstd-dev \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /opt/hyperhdr
COPY hyperhdr-source/ .

RUN mkdir build && cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr .. && \
    make -j$(nproc) && \
    make install || (echo "❌ make install failed" && ls -lR .)

# Stage 2: Runtime only
FROM ubuntu:22.04

ARG DEBIAN_FRONTEND=noninteractive
ENV TZ=Etc/UTC

RUN apt-get update && apt-get install -y --no-install-recommends \
    libqt5serialport5 \
    libqt5svg5 \
    libusb-1.0-0 libturbojpeg0 \
    libavcodec59 libavformat59 libswscale6 \
    libudev1 libasound2 \
    libglvnd0 libv4l-0 \
    libssl3 libflatbuffers1 libzstd1 \
    qtbase-abi-5-15-3 qttools5-dev-tools \
    && rm -rf /var/lib/apt/lists/*

COPY --from=builder /usr /usr

# Optional (if web UI or webserver is expected)
EXPOSE 8090 8092 19400 19444 19445 19333

CMD ["hyperhdr"]
