# Rukovoditel Dockerfile

FROM httpd

MAINTAINER filip.milasinovic@protonmail.ch

RUN apt-get update \
	&& apt-get upgrade -y \
	&& apt-get install php php-gd php-mbstring php-curl php-zip php-xml libapache2-mod-php php-mysql wget unzip -y

RUN a2enmod rewrite
RUN mkdir rukovoditel
RUN cd rukovoditel
RUN wget https://www.rukovoditel.net/download/free/rukovoditel_2.8.2.zip
RUN unzip rukovoditel_2.8.2.zip
RUN rm rukovoditel_2.8.2.zip

RUN mv * /var/www/html/

RUN chmod 777 /var/www/html/backups/ /var/www/html/uploads/ /var/www/html/uploads/attachments/ /var/www/html/uploads/users/ /var/www/html/uploads/images/ /var/www/html/cache/ /var/www/html/log/
RUN chown www-data:www-data -R /var/www/html/
RUN rm /var/www/html/index.html

ENV APACHE_RUN_USER www-data
ENV APACHE_RUN_GROUP www-data

EXPOSE 80

CMD /usr/sbin/apache2ctl -D FOREGROUND
