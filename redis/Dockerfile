FROM karolsteve/cmake-base:22.04
WORKDIR /app
RUN mkdir build && cd build && \
    git clone https://github.com/redis/hiredis.git && \
    cd hiredis && git reset --hard e0f4820 && \
    make -j$(nproc) && make install && \
    rm -Rf /app/build \

RUN mkdir build && cd build && \
    git clone https://github.com/sewenew/redis-plus-plus.git && \
    cd redis-plus-plus && git reset --hard 55f23c0 && \
    mkdir build && cd build && \
    cmake .. && \
    make -j$(nproc) && make install && \
    rm -Rf /app/build
