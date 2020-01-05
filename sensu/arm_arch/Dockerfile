FROM golang:1.13.5-alpine

LABEL maintainer="Roberto Chaud"
LABEL version="5.16.1"

ENV GOOS linux
ENV GOARCH arm

EXPOSE 2379 2380 3000 8080 8081 6060

RUN mkdir -p /var/sensu
WORKDIR /var/sensu

RUN curl -o v5.16.1.tar.gz https://github.com/sensu/sensu-go/archive/v5.16.1.tar.gz && \
    tar xzvf v5.16.1.tar.gz && \
    cd v5.16.1.tar.gz && \
    go build -o /usr/local/bin/sensu-agent ./cmd/sensu-agent && \
    go build -o /usr/local/bin/sensu-backend ./cmd/sensu-backend && \
    go build -o /usr/local/bin/sensuctl ./cmd/sensuctl

CMD ["sensu-backend"]

