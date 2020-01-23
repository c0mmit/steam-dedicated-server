## HOW TO: BUILD

```bash
$ docker build --build-arg STEAMAPPID=317670 -t mordhau-server .
```

## HOW TO: RUN SERVER

> save this yaml as mordhau.yaml

```yaml
version: "3"
services:
    mordhau-server:
        image: mordhau-server
        container_name: mordhau-server
        command: ["entry", "bash", "/app/entry"]
        volumes:
            - /etc/mordhau:/app:ro
            - /etc/mordhau/Game.ini:/config/Game.ini:rw
            - /etc/mordhau/Engine.ini:/config/Engine.ini:rw
        environment:
            - STEAMAPPID=629800
        network_mode: host
```

> then start with command

```bash
$ docker-compose -f mordhau.yaml up -d
```

if you want other games, just implement the `entry` script
and remember use command `entry bash /your/entry`.
