## Regex Manager

Custom regex managers to enhance renovate

### Update mirrored images in gitlab-ci.yml and Dockerfiles

In the form like `${REGISTRY_MIRROR_LIB}node:21.6.2-alpine` or `${REGISTRY_MIRROR}alpine/helm:3.14.2`

### Update IMAGE_XYZ for versions.sh scripts

The file needs to be named `versions.sh`

```
IMAGE_MAVEN=maven:3.9.6-eclipse-temurin-17-alpine
export IMAGE_NODE=node:21.6.2-alpine
```

### Update XYZ_VERSION for versions.sh scripts

The file needs to be named `versions.sh`

```
# renovate: datasource=github-tags depName=pgMemento/pgMemento extractVersion=^v(?<version>.*)$
PG_MEMENTO_VERSION=0.7.4
# renovate: datasource=helm depName=oauth2-proxy versioning=helm registryUrl=https://charts.bitnami.com/bitnami
OAUTH_PROXY_VERSION=4.9.0
# renovate: datasource=helm depName=keycloak versioning=helm registryUrl=https://charts.bitnami.com/bitnami
export KEYCLOAK_VERSION=18.7.1
```

### Update _VERSION variables in Dockerfiles

```
FROM python:3.12.2-alpine
# renovate: datasource=pypi depName=poetry
ENV POETRY_VERSION=1.8.0

RUN apk add --no-cache gcc musl-dev
RUN pip install "poetry==$POETRY_VERSION"
```

### Update EXTENSION versions in SQL

Works in `.sql` files

```
-- renovate: datasource=github-tags depName=pgMemento/pgMemento extractVersion=^v(?<version>.*)$
CREATE EXTENSION IF NOT EXISTS pgmemento WITH VERSION '0.7.4';
```

### Update version variables in .yaml files

```
test:
  version: 18.7.1 # renovate: datasource=helm depName=keycloak versioning=helm registryUrl=https://charts.bitnami.com/bitnami
```
