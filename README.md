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

## CRON Config

Add the following after installing and running nextcloud in docker:

    sudo crontab -e

Add this:

    */5 * * * * docker exec -u www-data nextcloud php cron.php

After that, set inside the settings the update type to CRON.

You can also use any other tool to run this task, but it must at least run every 5 minutes the `docker exec -u www-data nextcloud php cron.php` command.

## User

Replace the `user: "1004:1010"` with the correct user you are using for file access on your host. Nextcloud instance will automatically use the user www-data. The other container use this user, you can find it with it (first user, second group).

## Browser Caching

After installing the nextcloud instance multiple times on the same docker host, i encountered the problem, that the browser stores some data and will fail the install of nextcloud, making no changes inside the DB (error something like table not existent...). To solve this, delete Cache and everything else website-related from your browser prior install.
