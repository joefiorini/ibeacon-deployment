# Raspberry Pi iBeacon Setup

## Prerequisites

1. This is built for Raspberry Pi running [ArchLinux ARM](http://archlinuxarm.org)
2. It will try to install python & paramiko for you, but you may need to comment this out and do it yourself if you have problems (see the first block in `site.yml`)
3. Generate a UUID with `uuidgen` and update the inventory file (`beacons`) with the correct IP to your Raspberry Pi & the output from `uuidgen`

## Usage

After following the instructions above, run:

```
ansible-playbook -i beacons site.yml
```

You may need to append your Pi's user to that command (ie. `--user=root`)

This will leave you with:

1. A script to start advertising the iBeacon (`/usr/local/bin/start-beacon`)
2. A systemd service to control the beacon (`/etc/systemd/system/beacon`)

## Caveats

1. Should be making major, minor and power configurable as well, currently they are hardcoded in `roles/beacon/templates/start-beacon`
