# DataSHIELD R server - exposome environment

The DataSHIELD RServer has installed collections of tools to support DataSHIELD in combination with Exposome analysis.

## Contents
There are several DataSHIELD related dependencies installed
- [dsExposome](https://github.com/isglobal-brge/dsExposome)

## Usage
There are several platforms on which you can run RServer.

## Build
To build the docker images you need to execute this command:

```bash
docker build . -t brgelab/armadillo-rserver-exposome:*major-version* -t brgelab/armadillo-rserver-exposome:latest -t brgelab/armadillo-rserver-exposome:*tag*
# example
docker build . -t brgelab/armadillo-rserver-exposome:2 -t brgelab/armadillo-rserver-exposome:latest -t brgelab/armadillo-rserver-exposome:2.0.4
```

## Release
You can push the images to dockerhub using `docker push`.

`docker push brgelab/armadillo-rserver-exposome --all-tags`


### Deploy locally
You can steer the rserver at runtime using environment variables. You can toggle debug mode with the environment variable `DEBUG`.

Run the docker locally (docker only):

`docker run -e DEBUG=TRUE brgelab/armadillo-rserver-exposome:2`

Run in docker-compose `docker-compose.yml`:

```yaml
...
services:
  armadillo-rserver-exposome:
    environment: 
     - DEBUG = TRUE
...
```

### Deploy using Ansible

Check: https://galaxy.ansible.com/molgenis/armadillo

### Deploy using Kubernetes and helm

Check: https://github.com/molgenis/molgenis-ops-helm/tree/master/charts/molgenis-armadillo
