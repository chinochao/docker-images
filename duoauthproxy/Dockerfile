FROM centos:7 AS BUILDER

LABEL maintainer="Roberto Chaud"
LABEL version="5.3.1"

WORKDIR /opt

RUN yum install -y gcc make libffi-devel perl zlib-devel diffutils

RUN cd /opt && \
    curl https://dl.duosecurity.com/duoauthproxy-5.3.1-src.tgz -o duoauthproxy-5.3.1-src.tgz && \
    tar xzf duoauthproxy-5.3.1-src.tgz && \
    rm -rf duoauthproxy-5.3.1-src.tgz
    cd /opt/duoauthproxy-5.3.1* && \
    make && \
    cd duoauthproxy-build && \
    ./install --install-dir /opt/duoauthproxy --service-user duo_authproxy_svc --log-group duo_authproxy_grp --silent && \
    rm -rf /opt/duoauthproxy-5.3.1*

FROM centos:7 

LABEL maintainer="Roberto Chaud"
LABEL version="5.3.1"

WORKDIR /opt
COPY ansible/ /opt/
COPY docker-entrypoint/ /

RUN yum install -y ansible

USER duo_authproxy_svc:duo_authproxy_grp

RUN chown -R duo_authproxy_svc:duo_authproxy_grp /opt/

# Docker EntryPoint
ENTRYPOINT ["/docker-entrypoint"]

# Run server command from docker-entrypoint
CMD ["duoproxy"]

EXPOSE 1389 1636