# Alpine Linux

## Installation

### Alpine ≥ 3.18.0

*Barkery* will be available in the *community* repository since *Alpine 3.18.0*. The following packages are available:

- `barkery`: meta package installing *barkery* and the startup script package
- `barkery-browser`: standalone kiosk browser w/o startup scripts
- `barkery-weston`: startup script using [weston](https://gitlab.freedesktop.org/wayland/weston/)


### Alpine <3.18.0

Since *barkery* is a simple python script it is save to barkery from *edge* using [repository pinning](https://wiki.alpinelinux.org/wiki/Alpine_Package_Keeper#Repository_pinning). You need to at *edge* to you repository sources:

- add a pinned source to `/etc/apk/repositories`:
  ```python
  https://dl-cdn.alpinelinux.org/alpine/v3.17/main
  https://dl-cdn.alpinelinux.org/alpine/v3.17/community
  @edgecom http://dl-cdn.alpinelinux.org/alpine/edge/community
  ```
- install *barkery* from *edge*:
  ```python
  rpi [~]# apk add barkery@edgecom
  ```


## Configuration

The following configuration files exists:

- [`/etc/barkery/barkery.conf`](../ex/barkery.conf)
- [`/etc/barkery/weston.ini`](../ex/weston.ini)


## Run

Use `rc-update` to enable *barkery* on boot:

```python
rpi [~]# rc-update add barkery-weston
 * service barkery-weston added to runlevel default
```

Use `rc-service` to launch *barkery* manually:

```python
rpi [~]# rc-service barkery-weston start
 * Starting barkery-weston ...
```
