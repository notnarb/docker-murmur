# Docker-Murmur
[![Docker Repository on Quay](https://quay.io/repository/notnarb/murmur/status "Docker Repository on Quay")](https://quay.io/repository/notnarb/murmur) [![ImageLayers Size](https://img.shields.io/imagelayers/image-size/notnarb/docker-murmur/latest.svg)]()

## Description

Yet another Docker build for the popular Mumble server, Murmur.  This build
follows the currently released version in Alpine's repos (currently 1.2.10).

## Why another?

My preferred configuration is slightly different from others.

I also don't want to be subject to the (potentially malicious) changes another
repo could impose. People relying on relatively small Dockerhub repos is one big
security disaster waiting to happen.

## What's in this build

* Alpine base
* Latest version of Murmur in Alpine's repos (likely behind the latest released verison of Murmur)
* Changes user

## Configuration

One volume: /var/lib/murmur.  If there is a murmur.ini within the mounted
volume, it will be used instead of the slightly tweaked default ini included in
this repo.  The vanilla murmur.ini (pulled from the alpine repo) is also
provided in this repo as murmur.ini.default.

```
notnarb@redacted:~/w/murmur-docker$ diff murmur.ini murmur.ini.default
34c34
< # dbus=session
---
> dbus=session
96d95
< host=0.0.0.0
158d156
< bonjour=False
```

# Changelog

* 2016-03-02 - Trigger rebuild to get latest version of OpenSSL from Alpine repos (CVE-2016-0800 / DROWN)

# Other Docker + Murmur builds

Note: if you're looking at this repo, you probably want one of these instead!
They all offer the current latest version of murmur: 1.2.13

## mattikus/docker-murmur

Link: https://github.com/mattikus/docker-murmur

* Busybox base
* Current version of murmur (statically linked build)

## 7adietri/docker-murmur

Link: https://github.com/7adietri/docker-murmur

* Busybox base
* Current version of murmur (statically linked build)
* Accepts --build-args for replacing version at build time.
* Checksums the download!
* Changes user

## bddenhartog/docker-murmur

Link: https://github.com/bddenhartog/docker-murmur

* Alpine base
* Current version of murmur (statically linked build)
* Nice readme, easy build instructions, Makefile

## wmark/docker-murmur

Link: https://github.com/wmark/docker-murmur

* blitznote/debootstrap-amd64 base
* Latest Murmur (Uses the github API to get the latest linux release at build time!)
* Changes user
* Rkt compatibility
