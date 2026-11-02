# p910nd

A lightweight Umbrel Community App Store entry for sharing a USB-connected printer over the local network with **p910nd**.

The app exposes two separate services:

- **TCP 9100** — RAW / JetDirect printing. Add a network printer on your client using the Umbrel host's IP address and port `9100`.
- **TCP 8080 (Umbrel app page)** — a small information page. Opening the app tile must never connect a browser to the printer's RAW socket.

## Requirements

- UmbrelOS host with a USB printer connected.
- The printer must appear on the host as `/dev/usb/lp0`.
- The app's container runtime must be allowed to pass that device into the container.

## Install

1. Copy the `bunia-p910nd` directory into this app store repository.
2. Add the store to Umbrel using the repository URL.
3. Install **p910nd** from the Community App Store.
4. Configure your computer or phone to use a network printer at `UMBREL_IP:9100`.

## Important

This app currently maps `/dev/usb/lp0` directly. If your printer appears under a different device path, update the `devices` mapping and the p910nd `-f` argument in `docker-compose.yml`.

The host must expose the USB printer device to the app container. If Umbrel's container runtime does not pass `/dev/usb/lp0`, the service will start without access to the printer and printing will fail.

Port `9100` is a raw printing socket, **not HTTP**. Do not use it as the Umbrel app's web UI port.

## Repository

Maintained by [bun1a-dev](https://github.com/bun1a-dev).
