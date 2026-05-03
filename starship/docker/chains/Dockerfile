ARG BASE_IMAGE
ARG VERSION
FROM ${BASE_IMAGE}:${VERSION} AS source

FROM alpine:3.22

ARG BIN_PATH=/bin
ARG LIB_PATH=/lib

LABEL org.opencontainers.image.source="https://github.com/hyperweb-io/starship"

COPY --from=source ${BIN_PATH} /usr/bin
COPY --from=source ${LIB_PATH} /usr/lib

# Set up dependencies
ENV PACKAGES="curl make bash jq sed"

# Install minimum necessary dependencies
RUN apk add --no-cache $PACKAGES

WORKDIR /opt
