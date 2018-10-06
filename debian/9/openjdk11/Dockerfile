FROM debian:9.5-slim as builder

RUN apt-get update && \
    apt-get install -y curl
WORKDIR /tmp
RUN curl -L -O https://download.java.net/java/ga/jdk11/openjdk-11_linux-x64_bin.tar.gz



FROM debian:9.5-slim 

COPY --from=builder /tmp/openjdk-11_linux-x64_bin.tar.gz /root
RUN mkdir /usr/lib/jvm && \
    tar xvf /root/openjdk-11_linux-x64_bin.tar.gz -C /usr/lib/jvm && \
    rm -f /root/openjdk-11_linux-x64_bin.tar.gz && \
    update-alternatives --install /usr/bin/java java /usr/lib/jvm/jdk-11/bin/java 1 && \
    java -version
CMD ["bash"]
