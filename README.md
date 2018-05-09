# Mantis with Docker


## Install docker

```
sudo su root
curl -S -L get.docker.com | bash -
curl -L https://github.com/docker/compose/releases/download/1.21.2/docker-compose-`uname -s`-`uname -m` -o /usr/local/bin/docker-compose
chmod +x /usr/local/bin/docker-compose
```

## Prerequisites

```
apt-get update && apt-get install -y git

git clone https://gitlab.com/crocandr/docker-mantis.git /srv/mantis 
```

## Run

```
docker-compose -f /srv/mantis/docker-compose.yml up -d
```

After the first start wait some minutes (1-5) and after continue with Setup steps.

## Setup 


  1. Open the http://<your server IP> URL in your browser
  2. Set these parameters on the setup page:

    - Hostname (for Database Server): db
    - Username (for Database): mantisbt
    - Password (for Database): mantisbt
    - Database name (for Database): bugtracker
    - Default Time Zone: Budapest

  3. Click on "Install/Update Database" button
  4. wait some minutes to install the database
  5. after installation click on "back to the administration" (or something similar) button on the top right
  6. type "administrator" to the user and click on login button
  7. type "root" as password (please change it as soon as possible)
  8. after the successfull login, rename the admin folder

```
docker-compose exec mantisbt mv /var/www/html/admin /var/www/html/admin-moved
```


