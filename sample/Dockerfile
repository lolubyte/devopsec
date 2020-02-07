FROM lolubase-ubu:latest
MAINTAINER Daniel.Aboyewa <daniel.aboyewa@lolubyte.com>

ENV HTTPD_PREFIX /usr/local/apache2
ENV PATH $HTTPD_PREFIX/bin:$PATH

RUN mkdir -p "$HTTPD_PREFIX" \
        && chown www-data:www-data "$HTTPD_PREFIX"
WORKDIR $HTTPD_PREFIX

# Update  and install httpd runtime dependencies, Also install the necessary library for php  to ensur thath it works in apached

#We also install the library which php will use to connect to our database the mysql server

RUN apt-get update && apt-get install -y software-properties-common && apt-add-repository ppa:ondrej/php

RUN DEBIAN_FRONTEND="noninteractive" apt-get -y install tzdata

RUN apt-get update && apt-get -y install apache2 php libapache2-mod-php7.0 php7.0-mysql

EXPOSE 80

#Here we are copying a sample Demo  .php file from our source directory

COPY src/demo.php /var/www/html

#Here we run this apache  command in the foreground, this is to make sure that the container runs in the background

CMD /usr/sbin/apache2ctl -D FOREGROUND
