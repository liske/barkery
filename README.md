# barkery - digital signage based on WebKit2

This is project provides a *WebKit2* bases kiosk browser to be used for digital signage. It has a *MQTT* interface for remote management.

It is implemented in *Python3* and uses *Glib GObject Introspection* for the *Gtk3* and *Webkit2* stuff. It will run on *Raspberry Pi* using read only rootfs.

## Prerequisits

- *Python3*
- *Glib GObject Introspection*
  - *Gtk3*
  - *WebKit2*
- *Paho MQTT*

## Configuration

The configuration file is loaded from `/etc/barkery.conf`. Look at the [example config file](ex/bakery.conf) for available options.

## Features

### CEC

*Barkery* can issue HDMI CEC commands if CEC enabled hardware supported by *cec-client* is available. A CEC commands can be run on startup and via MQTT remote control.


### MQTT

*Barkery* can be configured to connect to a MQTT broker. It subscribes to the configured MQTT topics and performs defined actions when a message is published.

Topics:

- `barkery/terminal/{hostname}/load`
  `barkery/terminal/_bcast/cmd/load`

- `barkery/terminal/{hostname}/reset`
  `barkery/terminal/_bcast/cmd/reset`

- `barkery/terminal/{hostname}/sendkeys`
  `barkery/terminal/_bcast/cmd/sendkeys`

- `barkery/terminal/{hostname}/screenshot`
  `barkery/terminal/_bcast/cmd/screenshot`

