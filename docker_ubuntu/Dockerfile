FROM ubuntu:16.04

RUN apt-get update
RUN apt-get install apache2 -y
ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data
ENV APACHE_LOG_DIR /var/log/apache2
ENV APACHE_PID_FILE /var/run/apache2.pid
ENV APACHE_RUN_DIR /var/run/apache2
ENV APACHE_LOCK_DIR /var/www/html 
ENV APACHE_SERVERADMIN admin@localhost
ENV APACHE_SERVERNAME localhost
ENV APACHE_SERVERALIAS docker.localhost
ENV APACHE_DOCUMENTROOT /var/www

ADD apache2.conf /etc/apache2/apache2.conf
# Copy this repo into place.
ADD hosts /etc/hosts

EXPOSE 80

#Add user 
RUN useradd -ms /bin/bash  asdf
#CMD /bin/bash

# Update the default apache site with the config we created.
#ADD apache-config.conf /etc/apache2/sites-enabled/000-default.conf
CMD  ["source" "/etc/apache2/envvars"]

CMD ["/usr/sbin/apache2", "-D", "FOREGROUND"]

