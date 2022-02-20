FROM debian:bullseye

ARG WORKDIR
ENV WORKDIR $WORKDIR
ENV PATH $PATH:$WORKDIR
RUN mkdir -p $WORKDIR

RUN apt-get update && apt-get install -y  --no-install-recommends git
RUN apt-get install -y python3 python3-yaml python3-pip libpq-dev vim
#RUN libpython3-dev python3-setuptools vim
RUN pip3 install django==2.2 django-admin django-phone-field django-user-accounts django-modeladmin-reorder django-registration django-crispy-forms django-admin-sortable2 psycopg2
RUN GIT_SSL_NO_VERIFY=true git clone https://github.com/stoffels-it/call_for_volunteers
WORKDIR "/call_for_volunteers"
RUN git config http.sslVerify "false"
RUN ln -s apps/core .
RUN django-admin startproject call_for_volunteers .
