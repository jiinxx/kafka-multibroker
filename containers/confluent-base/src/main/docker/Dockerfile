FROM jiinx/java8

# Python
ENV PYTHON_VERSION="@python.version@"
ENV PYTHON_PIP_VERSION="@python.pip.version@"

# Confluent
ENV SCALA_VERSION="@scala.version@"
ENV CONFLUENT_MAJOR_VERSION="@confluent.version.major@"
ENV CONFLUENT_MINOR_VERSION="@confluent.version.minor@"

RUN yum update -y \
    && yum install -y epel-release \
    && yum install -y nc python-pip \
    && pip install --no-cache-dir --upgrade pip \
    && pip install --no-cache-dir jinja2 requests

RUN rpm --import http://packages.confluent.io/rpm/3.2/archive.key
COPY config/confluent.repo /etc/yum.repos.d/confluent.repo

COPY include/dub /usr/local/bin/dub
COPY include/cub /usr/local/bin/cub

COPY include/etc/confluent/docker /etc/confluent/docker
