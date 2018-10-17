FROM debian:9.5-slim as builder

RUN apt-get update && \
    apt-get install -y curl
WORKDIR /tmp
RUN curl -L -O https://download.java.net/java/GA/jdk11/13/GPL/openjdk-11.0.1_linux-x64_bin.tar.gz



FROM debian:9.5-slim 

COPY --from=builder /tmp/openjdk-11.0.1_linux-x64_bin.tar.gz /root
RUN mkdir /usr/lib/jvm
RUN tar xvf /root/openjdk-11.0.1_linux-x64_bin.tar.gz -C /usr/lib/jvm
RUN rm -f /root/openjdk-11.0.1_linux-x64_bin.tar.gz
ENV JAVA_HOME=/usr/lib/jvm/jdk-11.0.1
ENV PATH="$JAVA_HOME/bin:$PATH"

CMD ["bash"]
