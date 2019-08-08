# maxwell-docker
maxwell dockerfile with wait-for-it

docker-compose.yml
```
services:
  maxwell:
    image: liich/maxwell-docker
    depends_on: [ kafka ]
    restart: always
    volumes:
      - ./maxwell/maxwell_cfg.properties:/app/maxwell_cfg.properties
    entrypoint: [ ./wait-for-it.sh, kafka:9092, --, /app/bin/maxwell, --config, /app/maxwell_cfg.properties ]
```
