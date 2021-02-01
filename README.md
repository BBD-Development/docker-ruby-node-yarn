# Ruby + Node + Yarn Docker Image

Docker image with Ruby and Node.js with Yarn installed.

Based on the official Ruby image. Node and Yarn will be install on top using the same approach from the their official images.

Maintaned combinations:

- Ruby: 2.6       |    Node: 8.x    |    Yarn: >=1.22
- Ruby: 2.5 (EOL) |    Node: 8.x    |    Yarn: >=1.19

Note: More current version of Ruby and Node will be added later...

## Why Node.js and Ruby together?

Some applications, like Rails with Webpacker, requires both Ruby and Node.js to be installed in the same image in order to run or fully function.

## Tagging convention

There will be multiple variants of tag version to assist with selecting a specific docker image, depending on your applications needs.

The Ruby, Node and Yarn dependencies will be seperated by a `-` and will be used in the following order: `RUBY-NODE-YARN`

Example of using Ruby `2.6.0`, with Node `8.17.0` and Yarn `1.22.4` would be: `2.6.0-8.17.0-1.22.4`

## Supported tags and respective `Dockerfile` links

- [`latest`, `2.6.0-8.17.0-1.22.4` (2.6/Dockerfile)](https://github.com/BBD-Development/docker-ruby-node-yarn/blob/master/2.6/buster/Dockerfile)
- [`2.5.8-8.17.0-1.22.4` (2.5-8/Dockerfile)](https://github.com/BBD-Development/docker-ruby-node-yarn/blob/master/2.5-8/buster/Dockerfile)

## Image Variants

The `bbdinc/ruby-node-yarn` images come in two flavors: `debian` and `alpine`.

- `debian (buster)`
- `alpine`

Note: `stretch` and `slim` might come eventually later.

## Default Locale

This image uses `C.UTF-8` instead default `POSIX`.

## Ruby, Node and Yarn Release Versions
- [Ruby Releases](https://www.ruby-lang.org/en/downloads/releases/)
- [Node Releases](https://nodejs.org/en/download/releases/)
- [Yarn Releases](https://github.com/yarnpkg/yarn/releases)

## Release Process

- Update the specific Dockerfile with required dependency updates.
- Update the README's Supported tags and any other documentation required.
- Commit locally as one commit and indicate which versions have changed in the commit message
- Tag the commit with the same Docker tag that is being added (don't push yet)
    ```
    git tag 2.6.0-8.17.0-1.22.4
    ```
- Build the Docker changes locally and tag it the same way as you want it on docker but exclude the organization.
    ```
    docker build -f 2.6/buster/Dockerfile -t ruby-node-yarn:2.6.0-8.17.0-1.22.4 .
    ```
- If the build succeeds, then push you local Git repo with the pending commit/tag to the remote master branch
    ```
    git push --tags origin master
    ```
- Then list the local [docker images](https://docs.docker.com/engine/reference/commandline/images/) to get the docker image id and perform a [docker tag](https://docs.docker.com/engine/reference/commandline/tag/) using the Image ID and include the Organization this time.
    ```
    docker images
    REPOSITORY                    TAG                   IMAGE ID
    ruby-node-yarn                2.6.0-8.17.0-1.22.4   ad6a8f6f0c25

    docker tag ad6a8f6f0c25 bbdinc/ruby-node-yarn:2.6.0-8.17.0-1.22.4
    docker tag ad6a8f6f0c25 bbdinc/ruby-node-yarn:latest
    ```
- Final step, is to push the Docker tags to Dockerhub. Reminder, ensure you are logged into Dockerhub hub locally before attempting to push using [docker login](https://docs.docker.com/engine/reference/commandline/login/)
    ```
    docker push bbdinc/ruby-node-yarn:2.6.0-8.17.0-1.22.4
    docker push bbdinc/ruby-node-yarn:latest
    ```
