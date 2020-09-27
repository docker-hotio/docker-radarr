# radarr

<img src="https://raw.githubusercontent.com/hotio/docker-radarr/master/img/radarr.png" alt="Logo" height="130" width="130">

![Base](https://img.shields.io/badge/base-ubuntu-orange)
![Base](https://img.shields.io/badge/base-alpine-blue)
[![GitHub](https://img.shields.io/badge/source-github-lightgrey)](https://github.com/hotio/docker-radarr)
[![Docker Pulls](https://img.shields.io/docker/pulls/hotio/radarr)](https://hub.docker.com/r/hotio/radarr)
[![GitHub Registry](https://img.shields.io/badge/registry-ghcr.io-blue)](https://github.com/users/hotio/packages/container/radarr/versions)
[![Discord](https://img.shields.io/discord/610068305893523457?color=738ad6&label=discord&logo=discord&logoColor=white)](https://discord.gg/3SnkuKp)
[![Upstream](https://img.shields.io/badge/upstream-project-yellow)](https://github.com/Radarr/Radarr)

## Starting the container

Just the basics to get the container running:

```shell
docker run --rm --name radarr -p 7878:7878 -v /<host_folder_config>:/config hotio/radarr
```

The environment variables below are all optional, the values you see are the defaults.

```shell
-e PUID=1000
-e PGID=1000
-e UMASK=002
-e TZ="Etc/UTC"
-e ARGS=""
-e DEBUG="no"
```

## Tags

| Tag       | Description                                |
| ----------|--------------------------------------------|
| latest    | The same as `stable`                       |
| stable    | v0.2, the old one                          |
| unstable  | v3, nightly branch                         |
| musl      | v3, nightly branch, runs on Alpine         |

You can also find tags that reference a commit or version number.

## Configuration location

Your radarr configuration inside the container is stored in `/config/app`, to migrate from another container, you'd probably have to move your files from `/config` to `/config/app`.

## Executing your own scripts

If you have a need to do additional stuff when the container starts or stops, you can mount your script with `-v /docker/host/my-script.sh:/etc/cont-init.d/99-my-script` to execute your script on container start or `-v /docker/host/my-script.sh:/etc/cont-finish.d/99-my-script` to execute it when the container stops. An example script can be seen below.

```shell
#!/usr/bin/with-contenv bash

echo "Hello, this is me, your script."
```

## Troubleshooting a problem

By default all output is redirected to `/dev/null`, so you won't see anything from the application when using `docker logs`. Most applications write everything to a log file too. If you do want to see this output with `docker logs`, you can use `-e DEBUG="yes"` to enable this.
