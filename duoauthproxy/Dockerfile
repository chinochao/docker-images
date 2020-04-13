FROM centos:7

LABEL maintainer="Roberto Chaud"
LABEL version="3.2.4"

WORKDIR /opt
COPY ansible/ /opt/
COPY docker-entrypoint/ /

RUN yum install -y ansible wget gcc make python-devel libffi-devel perl zlib-devel

RUN cd /opt && \
    wget https://dl.duosecurity.com/duoauthproxy-3.2.4-src.tgz && \
    tar xzf duoauthproxy-3.2.4-src.tgz && \
    cd /opt/duoauthproxy-3.2.4-a79b571-src && \
    make && \
    cd duoauthproxy-build && \
    ./install --install-dir /opt/duoauthproxy --service-user duo_authproxy_svc --log-group duo_authproxy_grp --silent && \
    rm -rf /opt/duoauthproxy-3.2.4-a79b571-src/ /opt/duoauthproxy-3.2.4-src.tgz

RUN chown -R duo_authproxy_svc:duo_authproxy_grp /opt/

USER duo_authproxy_svc:duo_authproxy_grp

# Docker EntryPoint
ENTRYPOINT ["/docker-entrypoint"]

# Run server command from docker-entrypoint
CMD ["duoproxy"]

EXPOSE 1389 1636