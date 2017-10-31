FROM customdrupal

# Copy sites
COPY sites /var/www/html/sites/

# Create the private files directory and make files dir writeable
RUN mkdir /var/private_files && \
    chown -R www-data:www-data /var/www/html/sites/default/files && \
    chown -R www-data:www-data /var/private_files

COPY environment.env /var/environment.env
