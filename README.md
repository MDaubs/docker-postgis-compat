# Postgres 9.4.9 with PostGIS

Based on https://github.com/docker-library/postgres and https://github.com/appropriate/docker-postgis.

## Using on Linux

Start the server to use as the default Postgres instance:

```
docker run \
  --name postgres \
  -v /run/postgresql:/run/postgresql \
  -p 5432:5432 \
  -e POSTGRES_USER=$USER \
  -d mdaubs/postgis:9.4.9
```

Tweak the above if you want to run a bunch of Postgres instances or if you have
a system installed Postgres running on the default Unix socket and/or port.

Run pg_dump 9.4.9 from container:

```
docker run --rm \
  -v /run/postgresql:/run/postgresql \
  mdaubs/postgis:9.4.9 pg_dump
```

Tweak your `PATH` and drop this in a shell script if you want to always run
`pg_dump` from the container instead of your system's `pg_dump`.

## Using on OSX

Beats me but I'm guessing that bind mounting Unix sockets isn't going to work.
