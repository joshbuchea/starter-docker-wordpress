# Starter Docker WordPress

## Getting Started

- Build & Start Container(s), run in background: `docker-compose up -d`
- Start Container(s): `docker-compose start`
- Stop Containers: `docker-compose stop`
- Stop & Remove Containers: `docker-compose down`

## Ports

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
