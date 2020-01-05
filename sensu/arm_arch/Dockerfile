FROM golang:1.13.5-alpine

LABEL maintainer="Roberto Chaud"
LABEL version="5.16.1"

ENV GOOS linux
ENV GOARCH arm
# ENV PATH $PATH:/usr/local/go/bin

EXPOSE 2379 2380 3000 8080 8081 6060

RUN mkdir -p /var/sensu
WORKDIR /var/sensu

RUN wget -q -O v5.16.1.tar.gz https://github.com/sensu/sensu-go/archive/v5.16.1.tar.gz && \
    tar -C /var/sensu -xzf v5.16.1.tar.gz && \
    cd /var/sensu/sensu-go-5.16.1 && \
    # Sensu Build
    go build -o /usr/local/bin/sensu-agent ./cmd/sensu-agent && \
    go build -o /usr/local/bin/sensu-backend ./cmd/sensu-backend && \
    go build -o /usr/local/bin/sensuctl ./cmd/sensuctl && \
    # Clean UP
    rm -rf /var/sensu/* 

CMD ["sensu-backend"]