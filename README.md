# Remix-Dockerization
[![Docker Image CI](https://github.com/Konstantin-tr/Remix-Dockerization/actions/workflows/docker-image.yml/badge.svg)](https://github.com/Konstantin-tr/Remix-Dockerization/actions/workflows/docker-image.yml)

This repo demonstrates one possible way to dockerize a Remix application.
The approach used was inspired by the Dockerfile that is part of the [Indie Stack](https://github.com/remix-run/indie-stack/).
The Dockerfile in this repo is similar to the Indie Stack one but excludes the Prisma setup and has some other small changes.

## Getting started

To get started with this demo, run `docker build . -t [image-name:image-version]`.
If for some reason you do not have a package-lock.json file, you need to run `npm i` first.
After the image has been built, run `docker run -p 3000:3000 [image-name:image-version]` to start a container with the image you created.
