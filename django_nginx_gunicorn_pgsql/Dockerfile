FROM python:3.7.4-alpine

LABEL maintainer="Roberto Chaud"
LABEL version="0.2"

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

RUN mkdir -p /var/django/app
WORKDIR /var/django/app

ADD https://raw.githubusercontent.com/chinochao/docker-images/master/django_nginx_gunicorn_pgsql/requirements.txt .
ADD https://raw.githubusercontent.com/chinochao/docker-images/master/django_nginx_gunicorn_pgsql/Procfile /
ADD https://raw.githubusercontent.com/chinochao/docker-images/master/django_nginx_gunicorn_pgsql/docker-entrypoint /

RUN apk add --no-cache build-base 
                       postgresql-client 
                       postgresql-dev 
                       libldap 
                       openldap-clients 
                       libffi-dev 
                       openldap-dev 
                       musl-dev 
                       nginx; \
    pip install --no-cache-dir pip --upgrade; \
    pip install --no-cache-dir -r ./requirements.txt; \
    chmod +x /docker-entrypoint

ADD https://raw.githubusercontent.com/chinochao/docker-images/master/django_nginx_gunicorn_pgsql/nginx-default.conf /etc/nginx/nginx.conf

# Docker EntryPoint
ENTRYPOINT ["/docker-entrypoint"]

# Run server command from docker-entrypoint
CMD ["server"]

EXPOSE 8080