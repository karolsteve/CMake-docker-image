FROM ubuntu:22.04
WORKDIR /app
RUN apt update && apt upgrade && apt install -y \
     build-essential \
     ca-certificates \
     ccache \
     libboost-all-dev \
     libcurl4-openssl-dev \
     libssl-dev \
     libz-dev \
     lsb-release \
     openssl \
     screenfetch \
     wget \
     cmake \
     libprotobuf-dev \
     libprotoc-dev \
     libgrpc-dev \
     libgrpc++-dev \
     protobuf-compiler-grpc \
     libc6 \
     glibc-tools \
     git

RUN mkdir build && cd build && \
     git clone https://github.com/microsoft/cpprestsdk.git && \
     cd cpprestsdk && git reset --hard 096a9a1 && \
     mkdir -p build && cd build && \
     cmake .. -DCMAKE_BUILD_TYPE=Debug -DBUILD_TESTS=OFF -DBUILD_SAMPLES=OFF -DCPPREST_EXCLUDE_WEBSOCKETS=ON -DCMAKE_C_COMPILER_LAUNCHER=ccache -DCMAKE_CXX_COMPILER_LAUNCHER=ccache && \
     make -j`nproc` && make install && \
     rm -Rf /app/build

RUN /bin/sh -c mkdir build && cd build && \
     git clone https://github.com/etcd-cpp-apiv3/etcd-cpp-apiv3.git && \
     cd etcd-cpp-apiv3 && git reset --hard ca0e352 && \
     mkdir build && cd build && cmake .. && \
     make -j$(nproc) && make install && \
     rm -Rf /app/build # buildkit
