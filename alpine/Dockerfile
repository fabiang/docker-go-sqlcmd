# syntax=docker/dockerfile:1
ARG GOLANG_VERSION=1.23
FROM golang:$GOLANG_VERSION-alpine AS build

ARG GO_SQLCMD_VERSION=1.3.0
ARG GO_SQLCMD_SHA256=b184eedad43a2e545c39836c5c800b34a35d7c6e29b3a6027327f9365fdfa32b

ADD https://api.github.com/repos/microsoft/go-sqlcmd/tarball/v$GO_SQLCMD_VERSION /tmp/gosqlcmd.tar.gz

RUN echo "$GO_SQLCMD_SHA256  /tmp/gosqlcmd.tar.gz" > /tmp/gosqlcmd.sha256 \
    && sha256sum -w -c /tmp/gosqlcmd.sha256

WORKDIR /tmp/gosqlcmd/
RUN tar -xv --strip-components=1 -f /tmp/gosqlcmd.tar.gz -C /tmp/gosqlcmd/
RUN go build -o sqlcmd \
    -ldflags="-X main.version=$GO_SQLCMD_VERSION" \
    /tmp/gosqlcmd/cmd/modern

FROM alpine

COPY --from=build /tmp/gosqlcmd/sqlcmd /usr/local/bin/sqlcmd
COPY --from=build /tmp/gosqlcmd/LICENSE /usr/share/licenses/sqlcmd/LICENSE

ENTRYPOINT ["sqlcmd"]
