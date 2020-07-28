# Ruby + Node + Yarn Docker Image

Docker image with Ruby and Node.js with Yarn installed.

Based on the official Ruby image. Node and Yarn will be install on top using the same approach from the their official images.

Maintaned combinations:

- Ruby: 2.5 | Node: 8.x | Yarn: >=1.19

Note: More current version of Ruby and Node will be added later...

## Why Node.js and Ruby together?

Some applications, like Rails with Webpacker, requires both Ruby and Node.js to be installed in the same image in order to run or fully function.

## Tagging convention

There will be multiple variants of tag version to assist with selecting a specific docker image, depending on your applications needs.

The Ruby, Node and Yarn dependencies will be seperated by a `-` and will be used in the following order: `RUBY-NODE-YARN`

Example of using Ruby `2.5.8`, with Node `8.17.0` and Yarn `1.22.4` would be: `2.5.8-8.17.0-1.22.4`

## Supported tags and respective `Dockerfile` links

- [`latest`, `2.5.8-8.17.0-1.22.4` (2.5-8/Dockerfile)](https://github.com/BBD-Development/docker-ruby-node-yarn/blob/master/2.5-8/buster/Dockerfile)

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