FROM php:8.2-apache

# Active les modules Apache nécessaires
RUN a2enmod rewrite headers

# Augmente les tailles autorisées pour l'upload
RUN echo "upload_max_filesize=20M\npost_max_size=20M" > /usr/local/etc/php/conf.d/uploads.ini

RUN chown -R www-data:www-data /var/www/html/uploads && \
    chmod -R 755 /var/www/html/uploads

# Copie les fichiers de l'application
COPY ./ /var/www/html

# Autorise l'utilisation de .htaccess
RUN sed -i 's/AllowOverride None/AllowOverride All/g' /etc/apache2/apache2.conf
