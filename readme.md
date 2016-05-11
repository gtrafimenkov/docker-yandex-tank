# Yandex Tank in a Docker container

This is [Yandex Tank](https://tech.yandex.com/tank/) installed in a Docker container.

## How to use it

Create appropriate configuration file (ammo-file) and launch the Yandex Tank with command like:

```
docker run --rm -it -v $(pwd):/ammo gtrafimenkov/yandex-tank -c /ammo/ammo.ini
```

Example of ammo.ini:

```
[phantom]
address=IP_ADDRESS_OF_YOUR_SERVER
port=80
rps_schedule=const(100, 1m)
header_http = 1.1
headers = [Host: HOSTNAME_OF_YOUR_SERVER]
  [Connection: close]
uris = /

[monitoring]
config=none

[tank]
plugin_rcheck =
```

Example of ammo.ini to test an https server:

```
[phantom]
address=IP_ADDRESS_OF_YOUR_SERVER
port=443
ssl=1
rps_schedule=const(50, 1m)
header_http = 1.1
headers = [Host: HOSTNAME_OF_YOUR_SERVER]
  [Connection: close]
uris = /

[monitoring]
config=none

[tank]
plugin_rcheck =
```
