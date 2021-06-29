## arai2 with webui

docker compose script for setting up aria2 download client

- clone this repo `git clone https://github.com/zkhan93/aria2-webui.git .`
- edit `docker-compose.yml` file to specify following things
    - path for `downloads` volume
    - path for `completed` volume
    - aria2 rpc secret under environments of `aria-daemon` service
- run `docker-compose -d up` to start the 2 containers

