FROM ubuntu:focal

RUN apt-get update -q \
 && apt-get -y --no-install-recommends install \
    tinyproxy \
 && rm -rf /var/lib/apt/lists/*

RUN echo "Allow 0.0.0.0/0" >> /etc/tinyproxy/tinyproxy.conf

ENTRYPOINT ["/usr/bin/tinyproxy", "-d"]
