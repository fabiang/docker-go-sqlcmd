# fabian/sqlcmd

Sqlcmd – command line tool for Microsoft SQL Server.

[![fabiang/go-sqlcmd](https://img.shields.io/docker/pulls/fabiang/go-sqlcmd.svg)](https://registry.hub.docker.com/r/fabiang/go-sqlcmd)
[![fabiang/go-sqlcmd](https://badgen.net/github/license/fabiang/docker-go-sqlcmd)](https://github.com/fabiang/docker-go-sqlcmd)
[![Docker Image](https://github.com/fabiang/docker-go-sqlcmd/actions/workflows/docker.yml/badge.svg)](https://github.com/fabiang/docker-go-sqlcmd/actions/workflows/docker.yml)

## Available tags

* 1.1.1, 1.1.1-alpine, 1.1, 1.1-alpine , 1, 1-alpine, latest, latest-alpine

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
