FROM golang:1 as go

RUN \
  go get -u github.com/google/go-jsonnet/cmd/jsonnet; \
  go get -u github.com/jsonnet-bundler/jsonnet-bundler/cmd/jb; \
  go get -u github.com/brancz/gojsontoyaml

FROM ubuntu:focal

RUN apt-get update \
 && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    make \
    git \
    zip \
    unzip \
    build-essential \
    jq \
    openssh-client \
 && rm -rf /var/lib/apt/lists/*

# jsonnet tools
COPY --from=go /go/bin/jsonnet /usr/local/bin/jsonnet
COPY --from=go /go/bin/jb /usr/local/bin/jb
COPY --from=go /go/bin/gojsontoyaml /usr/local/bin/gojsontoyaml

# latest kubectl
RUN curl -Lo /usr/local/bin/kubectl "https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl" \
 && chmod +x /usr/local/bin/kubectl

# latest helm
RUN curl -L https://get.helm.sh/helm-v$(curl -s https://api.github.com/repos/helm/helm/releases/latest | jq -r '.tag_name')-linux-amd64.tar.gz | tar xz \
 && mv linux-amd64/helm /usr/local/bin/helm \
 && rm -rf linux-amd64

# kubeval
RUN curl -L https://github.com/instrumenta/kubeval/releases/latest/download/kubeval-linux-amd64.tar.gz | tar xz \
 && mv kubeval /usr/local/bin/kubeval

# latest sops
RUN curl -Lo /usr/local/bin/sops $(curl -s https://api.github.com/repos/mozilla/sops/releases/latest | jq -r '.assets[].browser_download_url' | grep linux) \
 && chmod +x /usr/local/bin/sops
