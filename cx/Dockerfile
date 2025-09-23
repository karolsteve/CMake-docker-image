FROM karolsteve/cmake-base:22.04
WORKDIR /app
RUN apt-get update && apt-get install -y \
    cmake build-essential libuv1-dev libssl-dev zlib1g-dev wget git

RUN mkdir build && cd build && \
    git clone https://github.com/datastax/cpp-driver.git && \
    cd cpp-driver && git reset --hard d9ae6b9 && \
    mkdir build && cd build && \
    cmake .. -DCMAKE_BUILD_TYPE=Release && \
    make -j$(nproc) && make install && \
    rm -Rf /app/build
