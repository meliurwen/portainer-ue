# Portainer - Unmetered Edition

Unofficial build of Portainer 100% telemetry-free!

## Customize

Simply place your custom files in [this](portainer/root_builder/custom) folder following the direcotry tree of the [Official Portainer's repo](https://github.com/portainer/portainer).

Your files will replace the original ones after the frontend app is patched, but before it is built.

+ **Custom Dir**: `portainer/root_builder/custom`

## Build and Run

Build the patched images and run:

```sh
docker-compose build --pull && docker-compose up -d
```

## Sources

+ **GitHub - Official Repo**
  + **Files**
    + [package.json](https://github.com/portainer/portainer/blob/develop/package.json)
    + [gruntfile.js](https://github.com/portainer/portainer/blob/develop/gruntfile.js)
    + [build.sh](https://github.com/portainer/portainer/blob/develop/build.sh)
    + [api/cmd/portainer/main.go](https://github.com/portainer/portainer/blob/develop/api/cmd/portainer/main.go)
    + [build/build_binary.sh](https://github.com/portainer/portainer/blob/develop/build/build_binary.sh)
  + **PR & Other stuff...**
    + [feat(core/telemetry): matomo usage POC #4135](https://github.com/portainer/portainer/pull/4135/files)
    + [feat(telemetry): replace GA with matomo #4140](https://github.com/portainer/portainer/pull/4140/files)
    + [Search by key "matomo"](https://github.com/portainer/portainer/search?q=matomo&unscoped_q=matomo)
