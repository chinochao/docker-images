FROM centos:7

LABEL maintainer="Roberto Chaud"
LABEL version="0.6"

RUN useradd -r -m -u 1001 awx && \
    mkdir -p /opt/custom-venvs && \
    mkdir -p /opt/setup && \
    chmod 777 -R /opt/setup /opt/custom-venvs

WORKDIR /opt/setup

COPY docker-entrypoint /
COPY ansible_template.j2 /opt/setup/

RUN yum install -y wget ansible curl python-setuptools epel-release \
                openssl openssl-devel gcc python-devel && \
    yum install -y python-virtualenv python36 python36-devel && \
    yum clean all && \
    rm -rf /var/cache/yum/x86_64/7/

USER awx

# Docker EntryPoint
ENTRYPOINT ["/docker-entrypoint"]

# Run setup command from docker-entrypoint
CMD ["setup"]
