FROM alpine:latest AS builder

ARG PB_VERSION=0.9.0

RUN apk add --no-cache \
    unzip \
    ca-certificates


# download and unzip PocketBase
ADD https://github.com/pocketbase/pocketbase/releases/download/v${PB_VERSION}/pocketbase_${PB_VERSION}_linux_amd64.zip /tmp/pb.zip
RUN unzip /tmp/pb.zip -d /pb/

FROM alpine:latest

RUN apk add --no-cache \
    ca-certificates

COPY --from=builder /pb/ /pb/

EXPOSE 8080

# start PocketBase
CMD ["/pb/pocketbase", "serve", "--http=0.0.0.0:8080", "--dir=/pb/pb_data", "--publicDir=/pb/pb_public"]