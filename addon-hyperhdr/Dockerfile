# ----------------------
# Updated Dockerfile
# ----------------------

FROM ubuntu:22.04

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

# Copy source files
COPY hyperhdr-source /opt/hyperhdr
WORKDIR /opt/hyperhdr

# Build HyperHDR with verbose logs
RUN mkdir build && cd build && \
    cmake -DCMAKE_BUILD_TYPE=Release -DCMAKE_INSTALL_PREFIX=/usr .. && \
    make -j$(nproc) VERBOSE=1 && \
    make install || ( \
        echo "❌ INSTALL FAILED - Listing content:" && \
        find . && \
        ls -lR /opt/hyperhdr/build && \
        ls -lR /usr/local /usr \
    )

# Keep the container running to inspect manually if needed (for testing only)
CMD ["bash"]
