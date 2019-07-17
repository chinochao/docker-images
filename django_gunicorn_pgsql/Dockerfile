FROM python:3.7.4-alpine

MAINTAINER Roberto Chaud version: 0.1

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

RUN mkdir -p /var/django/app
WORKDIR /var/django/app
ADD requirements.txt .

RUN apk add --no-cache build-base postgresql-client postgresql-dev libldap openldap-clients libffi-dev openldap-dev python2-dev musl-dev; \
    pip install --no-cache-dir pip --upgrade; \
    pip install --no-cache-dir -r ./requirements.txt;

EXPOSE 8080

CMD sh -c 'rm -rf /var/django/app/static/rest_framework /var/django/app/static/admin; \
           cp -r /usr/local/lib/python2.7/site-packages/rest_framework/static/rest_framework/ /var/django/app/static/; \
           cp -r /usr/local/lib/python2.7/site-packages/django/contrib/admin/static/admin/ /var/django/app/static/; \
           ./manage.py makemigrations; ./manage.py migrate ; \
           gunicorn -b [::]:8080 -k 'gevent' --timeout 120 -w ${WORKERS} ${APPNAME}.wsgi'
