# Drupal 8 docker package

### Install on Windows

Install [Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows).

Restart the machine when prompted to activate Hyper-V (Windows 10 Pro - 64bit required. Virtualbox or similar may be required on other systems).

### Install on other systems

Find the [relevant Docker installer](https://www.docker.com).

### Run

Run ```docker-compose up``` in the repo root.

Visit the site on ```localhost:8090```.

Visit phpmyadmin on ```localhost:8080```.

Log in as the super user with user name ```admin``` and password ```123``` if you are not logged in as default.

### Shut down

Shut down the docker network with ```docker-compose down```.

### Persistent storage
When running ```docker-compose up``` for the first time, the database is initialized from the sql image included in ```./docker/mysql```. This data persists in the sql data volume until the network is taken down with ```docker-compose down -v``` (warning: this will remove all data on your site with no warning prompt, be sure to take a backup).

You can start over with a new install by removing the `COPY` statement from `./docker/mysql/Dockerfile` and deleting the files `./docker/project/sites/default/settings.php` and `./docker/mysql/init.db`.

The included image, init.sql, is a clean standard install of Drupal 8, take a look at db.config.png to see how it was set up. The Devel and Hello World modules are enabled in the database image.

### Environment variables

All vars is moved to `./docker/project/environment.env` to try to streamline the setup.
You might want to change some of these. For example, all passwords are set to 123 and development options are on (no or limited caching).

### Drush and Drupal Console

Drush and Drupal Console are included in the image.

To use them, exec into the running container with  `docker exec -ti drupal8docker /bin/bash`.

### About

This project was created out of the [frustrations of getting drush to work with docker](https://stackoverflow.com/a/46322540/1685346). Feel free to use this project as you see fit without guaranties of any kind.
