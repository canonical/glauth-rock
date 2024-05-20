# Contributing

## Developing

Please refer to
the [rockcraft](https://canonical-craft-parts.readthedocs-hosted.com/en/latest/reference/index.html)
documentations to learn how to develop a ROCK image.

Please install `pre-commit` hooks to help enforce various validations:

```shell
pre-commit install -t commit-msg
```

## Building & Running Locally

You can build the ROCK image using the following command:

```shell
rockcraft pack -v
```

Assuming the [`skopeo`](https://snapcraft.io/install/skopeo/ubuntu) has been
installed. Import the created ROCK image into Docker:

```shell
sudo /snap/rockcraft/current/bin/skopeo --insecure-policy copy oci-archive:<local-rock-name>.rock docker-daemon:<image-name>:<image-tag>
```

Run a GLAuth container using Docker with [a minimum working config file](config/glauth.cfg):

```shell
docker run -d \
  --rm \
  -p 127.0.0.1:3893:3893/tcp \
  --name <container-name> \
  <image-name>:<image-tag>
```

> ⚠️ **NOTE**
>
> Please refer to the [GLAuth](https://github.com/glauth/glauth) for more
> details about the configuration file.

## Deploying

### Prerequisites

Before deploying the GLAuth ROCK image locally, there are several prerequisites:

- Enable the
  MicroK8s' [built-in registry](https://microk8s.io/docs/registry-built-in)

```shell
microk8s enable registry
```

- Tag the Docker image:

```shell
docker tag <image-name>:<image-tag> localhost:32000/<image-name>:<image-tag>
```

- Push the Docker image to the local built-in registry:

```shell
docker push localhost:32000/<image-name>:<image-tag>
```

### Deploy

Run the following command to deploy a locally-built ROCK image with
the [glauth-k8s-operator](https://github.com/canonical/glauth-k8s-operator)
charm:

```shell
juju deploy glauth-k8s --resource oci-image=localhost:32000/<image-name>:<image-tag>
```
