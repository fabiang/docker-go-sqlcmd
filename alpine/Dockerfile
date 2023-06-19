ARG GOLANG_VERSION=1.20
FROM golang:$GOLANG_VERSION-alpine AS build

ARG GO_SQLCMD_VERSION=1.1.0

ADD https://github.com/microsoft/go-sqlcmd/archive/refs/tags/v$GO_SQLCMD_VERSION.tar.gz /tmp/gosqlcmd.tar.gz

WORKDIR /tmp/gosqlcmd/
RUN tar -xv --strip-components=1 -f /tmp/gosqlcmd.tar.gz -C /tmp/gosqlcmd/
RUN go build -o sqlcmd -ldflags="-X main.version=$GO_SQLCMD_VERSION" /tmp/gosqlcmd/cmd/modern

FROM alpine

COPY --from=build /tmp/gosqlcmd/sqlcmd /usr/local/bin/sqlcmd
COPY --from=build /tmp/gosqlcmd/LICENSE /usr/share/licenses/sqlcmd/LICENSE

ENTRYPOINT ["sqlcmd"]
