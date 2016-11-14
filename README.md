Docker Restyaboard
==============================

This image includes a Restyaboard using postgres and elasticsearch.

* Restyaboard  
  http://restya.com/board/

* Docker  
  https://www.docker.com/


Quick Start
------------------------------

Build image and Run container using docker-compose.

``` bash
git clone https://github.com/asta-fulda/docker-restyaboard.git
cd docker-restyaboard
docker build .
```

Change Restyaboard Version
------------------------------

Currently running **v3.0**

To change that edit restyaboard/Dockerfile.  
Available version is https://github.com/RestyaPlatform/board/releases

Or pass a build variable:

```
ENV restyaboard_version=REPLACE_ME
```

In case of upgrade version, rebuild image and recreate container.


```sh
docker build
```

If you want to upgrade database, e.g.
(recommend to backup database before upgrade)

```sh
docker run --rm restyaboard bash

export PGHOST=$POSTGRES_PORT_5432_TCP_ADDR
export PGPORT=$POSTGRES_PORT_5432_TCP_PORT
export PGUSER=$POSTGRES_ENV_POSTGRES_USER
export PGPASSWORD=$POSTGRES_ENV_POSTGRES_PASSWORD
...
psql -d restyaboard -f sql/upgrade-0.1.3-0.1.4.sql
psql -d restyaboard -f sql/upgrade-0.1.4-0.1.5.sql
...
exit
```

License
------------------------------

[OSL 3.0](LICENSE.txt) fits in Restyaboard.
