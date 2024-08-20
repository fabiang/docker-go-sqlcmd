# fabian/go-sqlcmd

Sqlcmd – [Modern command line tool written in Go for Microsoft SQL Server](https://github.com/microsoft/go-sqlcmd).  
[Docker image for old sqlcmd is also available](https://github.com/fabiang/docker-sqlcmd).

[![fabiang/go-sqlcmd](https://img.shields.io/docker/pulls/fabiang/go-sqlcmd.svg)](https://hub.docker.com/r/fabiang/go-sqlcmd)
[![fabiang/go-sqlcmd](https://badgen.net/github/license/fabiang/docker-go-sqlcmd)](https://github.com/fabiang/docker-go-sqlcmd)
[![Docker Image](https://github.com/fabiang/docker-go-sqlcmd/actions/workflows/docker.yml/badge.svg)](https://github.com/fabiang/docker-go-sqlcmd/actions/workflows/docker.yml)

## Available tags

* 1.x.0, 1.x.0-alpine, 1.x, 1.x-alpine, 1, 1-alpine, latest, latest-alpine

See [Docker Hub page](https://hub.docker.com/r/fabiang/go-sqlcmd/tags?page=&page_size=&ordering=name&name=) for all available tags.

## License


All other parts of the library are licensed under [BSD 2-Clause License](LICENSE.md).

## Usage

Connect to an Sqlsrv inside another container (Container name is "my-sqlsrv"):

```bash
docker run -it --link my-sqlsrv:sqlsrv \
    -e SQLCMDPASSWORD='yourStrong(!)Password' \
    fabiang/go-sqlcmd -S sqlsrv -U sa
```

Or to any other server on the network:

```bash
docker run -it fabiang/go-sqlcmd -S some-sqlsrv -U sa
```

Get available options with:

```bash
docker run -it fabiang/go-sqlcmd '-?'
```
