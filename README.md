# p910nd

A lightweight Umbrel Community App Store package by [bun1a-dev](https://github.com/bun1a-dev).

Shares a USB-connected printer over the local network using p910nd.

## Ports

- **TCP 9100** — RAW / JetDirect printing. Configure your client with the Umbrel host IP and port `9100`.
- **TCP 8080** — app information page behind Umbrel's app proxy.

## Requirements

- USB printer connected to the Umbrel host.
- Printer available as `/dev/usb/lp0` on the host.
- Umbrel's app runtime must pass the device into the app container.

## Install

Add `https://github.com/bun1a-dev/umbrel-community-app-store` as a Community App Store, then install **p910nd**.

## Device path

If the printer is not `/dev/usb/lp0`, update both the `devices` mapping and the p910nd `-f` argument in `docker-compose.yml`.

## Note

Port `9100` is a raw printing socket, not HTTP. The app's web page is deliberately separate.
