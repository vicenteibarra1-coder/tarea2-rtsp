FROM ubuntu:24.04

RUN apt-get update && \
    apt-get install -y --no-install-recommends wget ca-certificates && \
    rm -rf /var/lib/apt/lists/*

WORKDIR /mediamtx

RUN wget -q https://github.com/bluenviron/mediamtx/releases/download/v1.9.3/mediamtx_v1.9.3_linux_amd64.tar.gz && \
    tar -xzf mediamtx_v1.9.3_linux_amd64.tar.gz && \
    rm mediamtx_v1.9.3_linux_amd64.tar.gz

EXPOSE 8554

ENTRYPOINT ["./mediamtx"]
