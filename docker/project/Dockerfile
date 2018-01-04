FROM customdrupal

# Copy sites
COPY sites /var/www/html/sites/

# Copy custom php.ini
COPY php.ini /usr/local/etc/php/php.ini

# Create the private files directory and make files dir writeable
RUN mkdir /var/private_files && \
    chown -R www-data:www-data /var/www/html && \
    chown -R www-data:www-data /var/private_files && \
    chown -R www-data:www-data /tmp && \
    touch /var/log/php-errors.log && \
    chown www-data:www-data /var/log/php-errors.log

COPY environment.env /var/environment.env
