# Ruby + Node + Yarn Docker Image

Docker image with Ruby and Node.js with Yarn installed.

Based on the official Ruby image. Node and Yarn will be installed on top using the same approach from their official images.

Maintained combinations:

| Ruby          | Node          | Yarn          | Status                |
| ------------- | ------------- | ------------- | --------------------- |
| `2.7.x`       | `8.x`         | `>=1.22`      | normal maintenance    |
| ~~`2.6.x`~~   | ~~`8.x`~~     | ~~`>=1.22`~~  | EOL: 2022-03-31       |
| ~~`2.5.x`~~   | ~~`8.x`~~     | ~~`>=1.19`~~  | EOL: 2021-03-31       |

Note: More current versions of Ruby and Node will be added later.

## Why Node.js and Ruby together?

Some applications, like Rails with Webpacker, requires both Ruby and Node.js to be installed in the same image in order to run or fully function.

## Tagging convention

There will be multiple variants of the tag versions to assist with selecting a specific docker image, depending on the needs of your application.

The Ruby, Node, and Yarn dependencies will be separated by a `-` and will be used in the following order: `RUBY-NODE-YARN`

An example of using Ruby `2.7.5`, with Node `8.17.0` and Yarn `1.22.4` would be: `2.7.5-8.17.0-1.22.4`

## Supported tags and respective `Dockerfile` links

- [`latest`, `2.7.5-8.17.0-1.22.4` (2.7-8/Dockerfile)](https://github.com/BBD-Development/docker-ruby-node-yarn/blob/master/2.7-8/buster/Dockerfile)

## Image Variants

The `bbdinc/ruby-node-yarn` images come in following flavors:

- `debian (buster)`

Note: `alpine`,`stretch` and `slim` might come later.

## Ruby, Node and Yarn Release Versions
- [Ruby Releases](https://www.ruby-lang.org/en/downloads/releases/)
- [Node Releases](https://nodejs.org/en/download/releases/)
- [Yarn Releases](https://github.com/yarnpkg/yarn/releases)

## Release Process

1. Update the specific Dockerfile with required dependency updates.
2. Update the README's Supported tags and any other documentation required.
3. Commit locally as one commit and indicate which versions have changed in the commit message
4. Build the Docker changes locally and tag it the same way as you want it on docker but exclude the organization.
    ```
    docker build -f 2.7/buster/Dockerfile -t ruby-node-yarn:2.7.5-8.17.0-1.22.4 .
    ```
5. Tag the commit with the same Docker tag that is being added (don't push yet)
    ```
    git tag 2.7.5-8.17.0-1.22.4
    ```
6. If the build succeeds, then push your local Git repo with the pending commit/tag to the remote master branch
    ```
    git push --tags origin master
    ```
7. Then list the local [docker images](https://docs.docker.com/engine/reference/commandline/images/) to get the docker image id and perform a [docker tag](https://docs.docker.com/engine/reference/commandline/tag/) using the Image ID and include the Organization this time.
    ```
    docker images
    REPOSITORY                    TAG                   IMAGE ID
    ruby-node-yarn                2.7.5-8.17.0-1.22.4   4596e277b67a

    docker tag 4596e277b67a bbdinc/ruby-node-yarn:2.7.5-8.17.0-1.22.4
    docker tag 4596e277b67a bbdinc/ruby-node-yarn:latest
    ```
8. Final step, is to push the Docker tags to Dockerhub. Reminder, ensure you are logged into Dockerhub hub locally before attempting to push using [docker login](https://docs.docker.com/engine/reference/commandline/login/)
    ```
    docker push bbdinc/ruby-node-yarn:2.7.5-8.17.0-1.22.4
    docker push bbdinc/ruby-node-yarn:latest
    ```
