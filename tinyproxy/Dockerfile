FROM ubuntu:focal

RUN apt-get update -q \
 && apt-get -y --no-install-recommends install \
    tinyproxy \
 && rm -rf /var/lib/apt/lists/*

ENTRYPOINT ["/usr/bin/tinyproxy", "-d"]
