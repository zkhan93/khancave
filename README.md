## Web Services on Home Server

Runs the following services

- Nextcloud
- Calibre Web
- Aria2 cient and Web UI

### how to deploy

- clone this repo `git clone https://github.com/zkhan93/aria2-webui.git .`
- edit `docker-compose.yml` file to specify following things
    - path for `downloads` volume
    - path for `completed` volume
    - aria2 rpc secret under environments of `aria-daemon` service
- run `docker-compose -d up` to start the 2 containers

#### Hacks

nextcloud needs a cron job to run at every 5 mins for its background jobs
so instead of adding the following service in docker-compose
```
  cron:
    build: ./app
    restart: always
    volumes:
      - nextcloud:/var/www/html
    entrypoint: /cron.sh
    depends_on:
      - db
      - redis
```
I just added a task/cron job in host directly as `docker exec -u www-data services_nextcloud_1 php cron.php`
which does the job but will have to remember doing that after every deploy.
