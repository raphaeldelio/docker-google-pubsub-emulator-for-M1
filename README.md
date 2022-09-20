# Google Cloud Pub/Sub for Docker compatible with M1
This repo was forked from [Docker Google Pubsub Emulator](https://github.com/broadlume/docker-google-pubsub-emulator)

The original repo hadn't been updated for years and was lacking support for M1 processors.

This new image has support for M1

# Google Cloud Pub/Sub for Docker

This repo contains a _ridiculously small_ Docker image for the [Cloud Pub/Sub Emulator](https://cloud.google.com/pubsub/docs/emulator) for usage in development.

_Only use this image in development, do not use this in production!_

## Usage

1. With `docker-compose`:

   ```yaml
   ---
   version: '3.6'

   services:
     pubsub:
       image: raphaeldelio/google-pubsub-emulator
       ports:
         - 8085:8085
   ```

2. Plain `docker` command:

   ```sh
   docker run -p 8085:8085 raphaeldelio/google-pubsub-emulator
   ```

3. Make sure to set these environment variables in your app that requires the
   pubsub service

   ```sh
   export PUBSUB_EMULATOR_HOST=localhost:8085
   ```


## Build image for multiple architectures
1. Create a builder

```sh
docker buildx create --name mybuilder
```

2. Tell buildx to use "mybuilder"

```sh
docker buildx use mybuilder
```

3. Build and push the image
```sh
docker buildx build --push --tag [docker-hubid/image-tag] --platform=linux/arm64,linux/amd64 .
```

## Related Tutorials
- [How to connect your Spring Cloud Application to a local Google Cloud Pub/Sub Emulator](https://raphaeldelio.com/how-to-connect-your-spring-cloud-application-to-a-local-google-cloud-pub-sub-emulator-512926cce2b4)

## Related Repositories
- [Google Cloud Pub Sub Emulator with Spring Cloud](https://github.com/raphaeldelio/Google-Cloud-Pub-Sub-Emulator-with-Spring-Cloud)