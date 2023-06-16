[![Docker Image CI](https://github.com/cmoras/all-things-flink/actions/workflows/docker-image.yml/badge.svg)](https://github.com/cmoras/all-things-flink/actions/workflows/docker-image.yml)

# all-things-flink
all-things-flink


# How to build a multi architecture docker image.

clen.moras@MBT727VPGY21 hive % docker buildx build --push \
  --platform linux/amd64,linux/arm64,linux/arm/v7,linux/arm/v6,linux/ppc64le,linux/s390x \
  --tag clen/flink:random_image .
