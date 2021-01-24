FROM ubuntu:focal

RUN apt-get update -q \
 && apt-get -y --no-install-recommends install \
    git make build-essential ca-certificates \
 && git clone https://github.com/robertdavidgraham/masscan \
 && cd masscan \
 && make

FROM ubuntu:focal

RUN apt-get update -q \
 && apt-get -y --no-install-recommends install \
    libpcap-dev \
 && rm -rf /var/lib/apt/lists/*

COPY --from=0 /masscan/bin/masscan /bin/masscan
COPY --from=0 /masscan/data/exclude.conf /etc/exclude.conf

ENTRYPOINT ["/bin/masscan"]
