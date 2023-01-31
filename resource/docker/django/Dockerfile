FROM python:3.11-buster

# env
ENV PIP_DISABLE_PIP_VERSION_CHECK 1
ENV PYTHONUNBUFFERED 1

# copy source and install dependencies
RUN mkdir -p /opt/project
RUN mkdir -p /opt/project/pip_cache
RUN mkdir -p /opt/project/${DJANGO_PROJECT_NAME}
COPY . /opt/project
WORKDIR /opt/project
RUN pip install -r /opt/project/resource/docker/django/requirements.txt --cache-dir /opt/project/pip_cache
RUN chown -R www-data:www-data /opt/project

# start server
EXPOSE 8020
STOPSIGNAL SIGTERM

CMD ["/opt/project/resource/docker/django/start-server.sh"]