FROM centos:7

LABEL maintainer="Roberto Chaud"
LABEL version="1.5"

RUN useradd -r -m -u 1001 awx && \
    mkdir -p /opt/custom-venvs && \
    mkdir -p /opt/setup && \
    chmod 777 -R /opt/setup /opt/custom-venvs

WORKDIR /opt/setup

COPY docker-entrypoint /
COPY ansible_template.j2 /opt/setup/
RUN chmod 0777 /docker-entrypoint && \
    chmod 0777 /opt/setup/ansible_template.j2

RUN umask 022 && \
    yum update -y && \
    yum install -y wget curl python-setuptools epel-release \
                openssl openssl-devel gcc python-devel && \
    yum install -y python-virtualenv python36 python36-devel && \
    pip3 install --upgrade pip && \
    pip3 install ansible==2.9.16 && \
    yum clean all && \
    rm -rf /var/cache/yum/x86_64/7/

USER awx

# Docker EntryPoint
ENTRYPOINT ["/docker-entrypoint"]

# Run setup command from docker-entrypoint
CMD ["setup"]
