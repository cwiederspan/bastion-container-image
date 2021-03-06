# Bastion Container

![Build Bastion Container](https://github.com/cwiederspan/bastion-container-image/workflows/Build%20and%20Push%20Container%20Image/badge.svg)

A project for creating a bastion host container image that can be used to troubleshoot and test applications.

## Build Locally

```bash

docker build -t cwiederspan/bastion-container-image:latest .

docker push cwiederspan/bastion-container-image:latest

docker run -it --rm cwiederspan/bastion-container-image:latest

```

## Test Locally

```bash

docker build -t cwiederspan/bastion-container-image:local .

docker run -it --rm cwiederspan/bastion-container-image:local

```

## Using the Container

```bash

az container create \
  -n cdw-privateapp-20210119-aci \
  -g cdw-privateapp-20210119 \
  -l westus2 \
  --image cwiederspan/bastion:latest \
  --vnet cdw-privateapp-20210119-vnet \
  --subnet bastion

az container exec -n cdw-privateapp-20210119-aci -g cdw-privateapp-20210119 --exec-command './bin/bash'

```

## GitHub Actions

This project uses GitHub Actions and the [`pipeline.yml`](.github/workflows/pipeline.yml) file to build and push
this image to [Docker Hub](https://hub.docker.com/r/cwiederspan/bastion).

## Follow Up

Email chwieder@microsoft.com for more information on this container and scenarios for usage.
