# Drupal 8 docker package

### Install on Windows

Install [Docker](https://store.docker.com/editions/community/docker-ce-desktop-windows).

Restart the machine when prompted to activate Hyper-V (Windows 10 Pro - 64bit required. Virtualbox or similar may be required on other systems).

### Run

Run ```docker-compose up``` in the repo root.

Visit the site on ```localhost:8090```.

Visit phpmyadmin on ```localhost:8080```.

Log in as the super user with user name ```admin``` and password ```123```.

### Shut down

Shut down the docker network with ```docker-compose down```.

### Persistent storage
When running ```docker-compose up``` for the first time, the database is initialized from the sql image included in ```./docker/mysql```. This data persists in the sql data volume until the network is taken down with ```docker-compose down -v``` (warning: this will remove all data on your site with no warning prompt, be sure to take a backup).

You can start over with a new install by removing the `COPY` statement from `./docker/mysql/Dockerfile` and deleting the files `./docker/project/sites/default/settings.php` and `./docker/mysql/init.db`.

The included image, init.sql, is a clean standard install of Drupal 8, take a look at db.config.png to see how it was set up.
All passwords is set to 123, remember to change these.

### Environment variables

All vars is moved to `./docker/project/environment.env` to try to streamline the setup.

### Drush

Drush is included in the image, to use it exec into the running container.

Find the container ID by running `docker container ls`.

Exec into the container by running `docker exec -ti xyz /bin/bash` where `xyz` is the first couple of digits in the ID hex. Now you can drush.
