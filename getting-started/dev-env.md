# Development environment

## Start external micro-services

elasticMS comes with multiple micro-services:

* Redis: cache and session
* elasticsearch: for indexing contents
* Tika: for extracting data from assets
* PosgresSQL or MySQL: As authentic source of data

In order to simplify development all those services are available in a docker compose:

```bash
cd docker
cp .env.dist .env
docker compose up -d
```

### Test your config

* [Traefik](http://localhost:8888/dashboard/#/): The middleware application used to route packages
* [Kibana](http://kibana.localhost/app/dev_tools#/console): Power tools for elasticsearch
* [es01](http://es01.localhost/),[es02](http://es02.localhost/),[es03](http://es03.localhost/): the hearts of elasticMS
* [Mailhog](http://mailhog.localhost/): A mail catcher
* [MinIO](http://minio.localhost/login): A S3 like service
* [Tika](http://tika.localhost): A S3 like service
* [Redis Commander](http://redis-commander.localhost): A Redis inspector tool


### Local ports exposed

| Port | service         |
|------|-----------------|
| 80   | traefik         |
| 442  | traefik TLS     |
| 1025 | mailhog         |
| 3306 | mariadb         |
| 5432 | postgres        |
| 5601 | kibana          |
| 6379 | redis           |
| 8888 | traefik's admin |
| 9000 | minio           |
| 9998 | tika            |

## Prerequisite 

```bash
cd ~
wget https://get.symfony.com/cli/installer -O - | bash
sudo mv ~/.symfony5/bin/symfony /usr/local/bin/symfony 
```

## Init elasticMS

Go to [MinIO](http://minio.localhost/login) with the `accesskey` user and the `secretkey` password:

* Click on "Create Bucket"
* Specify `demo` as bucket name
* Click on "Create Bucket"

In order to initialize a Db open a terminal: 

````bash
cd docker
cp .env.dist .env
sh pg_init.sh demo public
````

Init the DB and create an admin user:

````bash
cd ../elasticms-admin
cp .env.dist .env
php bin/console doctrine:migrations:migrate
php bin/console emsco:user:create --super-admin
php bin/console asset:install --symlink
symfony server:start --port=8080 -d --no-tls
````

[elasticMS Admin](http://localhost:8080) is now available.


Useful commands:

* `symfony server:log`

## Load and save DB dumps

You may want to load an existing elasticMS dump. If so please check the dump's schema matches the DB's schema.

```bash
cd docker
sh pg_load.sh demo dump_demo.sql
```


To make a dump:

```bash
cd docker
sh pg_dump.sh demo demo > dump_demo.sql
```
