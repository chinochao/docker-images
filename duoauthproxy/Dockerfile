FROM centos7

LABEL maintainer="Roberto Chaud"
LABEL version="3.2.4"




RUN yum install wget gcc make python-devel libffi-devel perl zlib-devel

RUN cd /opt && \
    wget https://dl.duosecurity.com/duoauthproxy-3.2.4-src.tgz && \
    tar xzf duoauthproxy-3.2.4-src.tgz && \
    cd duoauthproxy-3.2.4-a79b571-src && \
    make && \
    cd duoauthproxy-build && \
    ./install