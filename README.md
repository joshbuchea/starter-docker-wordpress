# Starter Docker WordPress

## Getting Started

- Build & Start Container(s), run in background: `docker-compose up -d`
- Start Container(s): `docker-compose start`
- Stop Containers: `docker-compose stop`
- Stop & Remove Containers: `docker-compose down`

## Containers

- MySQL: Port `3306`
- WordPress: Port `8000`
- phpMyAdmin: Port `8080`
- Search & Replace DB: Port `8081`

## Backup Container

- Docker Hub: https://hub.docker.com/r/aveltens/wordpress-backup/
- GitHub Repo: https://github.com/angelo-v/wordpress-backup

Commands:

- Backup WordPress (HTML & DB): `docker exec [backup_container_id] backup`
- Restore WordPress from backup: `docker exec [backup_container_id] restore [yyyyMMdd]`

Features:

- Automatic Backups
- Automatic Cleanup
- Manual backup w/ one command
- Manual restore w/ one command

The backup container makes a few assumptions:

- mysql container has a hostname of `mysql`
- mysql service has optional user/pwd defined

## From docker-compose.yml

```
###
# What's included:
# - WordPress container (defaults to port 8000)
# - database container (connected automagically to WordPress)
# - phpmyadmin container (defaults to port 8080)
# - searchreplacedb container (defaults to port 8081, connects automagically to mysql)
#
#
# Instructions:
#
# Make your directory look like this:
#
# - ./docker-compose.yml (this file)
# - ./www (should contain www files for developing)
# - ./initdb (All sql files in here will be run when docker-compose is first ran)
# - ./initdb/dump.sql (Example of putting your mysql dump in here)
#
# Note on importing SQL files:
#   By default the WordPress and SearchReplaceDB contianers use the database called `wordpress`.
#   It is reccomened that your sql init file starts with 'USE `wordpress`;' to make sure
#   the correct database is selected.
#
# To get started, run:
# docker-compose up -d
#
#
# Troubleshooting:
#
# WordPress and/or phpmyadmin indicate there's no mysql connection
# - If you have sql files in initdb, it may take a while to import, delaying mysql to start.
#   You can check the status of mysql with docker logs
#
# SearchReplaceDB is giving me errors on my wordpress tables
# - It's possible your import sql files
#
# How do I re-import?
# - To reimport, you just need to stop the docker containers (docker-compose down),
#   delete the .data directory created by mysql, and then run docker-compose up -d.
##
```
