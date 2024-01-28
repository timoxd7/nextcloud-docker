# Nextcloud Docker

This is a simple repo to have some docker-compose files and configuration needed to quickly fire up a nextcloud instance.

## What to use for?

These are for personal use and only small-scale instances.

## Which to use?

- nextcloud-direct → HTTP-Access without proxy (minimal setup)
- nextcloud-reverse-proxy → HTTPS-Access with Auto-signed certificate (for public use)
- nextcloud-reverse-proxy-selfsigned → HTTPS-Access with self-signed certificate (for use in private network)

## Configuration

Change the config in the .env.sample to your desired needs and save it as .env file.

## Nginx config

Some additional config for nginx is needed. Just copy default.conf.sample to default.conf to let it be overwritten by nginx without loosing the origin file.
