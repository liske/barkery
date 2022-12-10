# barkery - WebKit2-based kiosk browser for digital signage

This is project provides a *WebKit2*-based kiosk browser to be used for digital signage. It has a simple *MQTT* interface for remote management.

It is implemented in *Python3* and uses *Glib GObject Introspection* to use *Gtk3* and *Webkit2*. Using [Alpine Linux](https://www.alpinelinux.org/) it is possible to run barkery on a read-only rootfs on *Raspberry Pi* or other ARM SoCs.

## Prerequisits

- *Python3*
- *Glib GObject Introspection*
  - *Gtk3*
  - *WebKit2*
- *Paho MQTT*

## Installation

*Barkery* is available in the following linux distributions:

- [Alpine Linux](docs/Alpine.md)

On other platforms you could install it's [python dependencies](requirements.txt) using the package manager (*apt-get* et. al.) or using *pip3*. *Barkery* is a single python script which can be run if the requirements are met, no special installation is needed.

*Merge requests with instructions for other Linux distributions are very welcome.*

## Configuration

The configuration file is loaded from `/etc/barkery/barkery.conf`. Look at the [example config file](ex/barkery.conf) for available options.

## Features

### MQTT

*Barkery* can be configured to connect to a MQTT broker. It subscribes to the configured MQTT topics and performs defined actions when a message is published.

Command topics subscribed by barkery:

- load the URL from the message body
  - `barkery/terminal/{hostname}/load`
  - `barkery/terminal/_bcast/cmd/load`

- load barkery's startup page
  - `barkery/terminal/{hostname}/reset`
  - `barkery/terminal/_bcast/cmd/reset`


State topics published by barkery:
- barkery's state as JSON structure
  - `barkery/terminal/{hostname}/status`
