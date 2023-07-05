# Use PHP 8.1 as default PHP version
# Use Apache as the web server
FROM php:8.1-apache

# Install dependencies that needed & configure Apache modules
RUN apt-get update && \
libapache2-mod-security2 && \
docker-php-ext-install mysqli pdo pdo_mysql && \
a2enmod rewrite && \
a2enmod headers && \
apt install git -y && \
chmod -R 755 /var/www/html && \
git clone https://github.com/coreruleset/coreruleset /usr/share/modsecurity-crs && \
mv /usr/share/modsecurity-crs/crs-setup.conf.example /usr/share/modsecurity-crs/crs-setup.conf && \
mv /usr/share/modsecurity-crs/rules/REQUEST-900-EXCLUSION-RULES-BEFORE-CRS.conf.example /usr/share/modsecurity-crs/rules/REQUEST-900-EXCLUSION-RULES-BEFORE-CRS.conf

CMD ["apache2ctl", "-D", "FOREGROUND"]