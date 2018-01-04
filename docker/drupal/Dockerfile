FROM drupal:8.4.3-apache

# Install packages
RUN rm /bin/sh && ln -s /bin/bash /bin/sh && \
    apt-get update && apt-get install --no-install-recommends -y \
    curl \
    wget \
    vim \
    git \
    unzip \
    mysql-client

# Install PHP extensions
# RUN docker-php-ext-install \
#     mcrypt

# Clean repository
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

#---------------------- Install development tools ----------------------

# Install Composer
RUN curl -sS https://getcomposer.org/installer | php && \
    mv composer.phar /usr/local/bin/composer && \
    ln -s /root/.composer/vendor/bin/drush /usr/local/bin/drush

#  Install Drush
RUN composer global require drush/drush && \
    composer global update

# Install Drupal Console Launcher
RUN curl https://drupalconsole.com/installer -L -o drupal.phar && \
    mv drupal.phar /usr/local/bin/drupal && \
    chmod +x /usr/local/bin/drupal

# Install Drupal Console
RUN cd /var/www/html && \
    composer require drupal/console:~1.0 --prefer-dist --optimize-autoloader && \
    drupal init




# composer global config minimum-stability dev && \
# composer global config prefer-stable true && \


