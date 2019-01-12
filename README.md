# Overview

Docker Application for running a [Parseplatform.org](http://parseplatform.org) Server (production & development).

Comes with MongoDB, Parse Dashboard, and SSL httpd proxy.

Each Parse app utilizes its own database.

Based on [Bitnami](https://bitnami.com/stack/parse/containers) images.


# Deployment

## Configuration

- Copy `sample.env` to `.env` and modify accordingly

- Start / stop the apps

- Each app will now have an auto-generated default config file (with info derived from the `.env` file)

- **Make a note** of the MongoDB database URI provided by these auto-generated config files  

- Modify these default config files accordingly (see `sample` configs in this repo.) and restart the apps.

- For **Parse Dashboard**, the `serverURL` parameter in `config.json`  should be pointing at the **public** URL for the Parse server(s), not the Docker container name.


## Start everything

`docker-compose up -d`


# Quick Test

## Direct to server:

```
curl -X GET \
-H "X-Parse-Application-Id: parseapp" \
-H "X-Parse-REST-API-Key: [rest api key]" \
-H "Content-Type: application/json" \
-d '{}' \
http://[hostname]:1337/parse/classes/WallPost
```

## Via SSL Proxy:

```
curl -X GET \
-H "X-Parse-Application-Id: parseapp" \
-H "X-Parse-REST-API-Key: [rest api key]" \
-H "Content-Type: application/json" \
-d '{}' \
-k \
https://[hostname]/parse/classes/WallPost
```


### More documentation to be added…
