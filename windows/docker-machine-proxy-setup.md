# Docker machine proxy setup

To permanently setup a proxy for a docker-machine add following lines to `%USER%/.docker/machine/machines/*machinename*/config.json`:
```
      "Env": [
          "HTTP_PROXY=http://username:password@proxy:80",
          "HTTPS_PROXY=http://username:password@proxy:80",
          "NO_PROXY=10.2.*"
      ],
```
