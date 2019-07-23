FROM python:3.7.4-alpine

LABEL maintainer="Roberto Chaud"
LABEL version="0.1"

ENV PYTHONUNBUFFERED 1
ENV PYTHONDONTWRITEBYTECODE 1

RUN mkdir -p /var/django/app
WORKDIR /var/django/app
ADD https://raw.githubusercontent.com/chinochao/docker-images/master/django_gunicorn_pgsql/requirements.txt .

RUN apk add --no-cache build-base postgresql-client postgresql-dev libldap openldap-clients libffi-dev openldap-dev python2-dev musl-dev; \
    pip install --no-cache-dir pip --upgrade; \
    pip install --no-cache-dir -r ./requirements.txt;

EXPOSE 8080

CMD sh -c './manage.py collectstatic --noinput; \
           ./manage.py makemigrations; ./manage.py migrate ; \
           gunicorn -b [::]:8080 -k 'gevent' --timeout 120 -w ${WORKERS} ${APPNAME}.wsgi'
