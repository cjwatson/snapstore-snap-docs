---
title: Troubleshooting the Snap Store Proxy
table_of_contents: true
---

# Troubleshooting

To check egress firewall rules:

    snap-proxy check-connections

Logs are available in systemd logs:

    snap logs snap-store-proxy

or:

    journalctl -u 'snap.snap-store-proxy.*'


The snap-proxy snap includes multiple systemd services, the status of
which can be checked with:

    snap-proxy status

Or:

    sudo systemctl status -a 'snap.snap-store-proxy.*'

To restart the snap-proxy services, run:

    sudo snap restart snap-proxy

The download cache is at `/var/snap/snap-store-proxy/nginx/cache`. The default
limit is 2GB, this can be changed with:

    sudo snap-proxy config proxy.cache.size=4096  # in mb

## Documentation

This documentation is shipped with the snap, and available at:

    http://MY-PROXY/docs/

## Bug reporting

Please file bugs against this project on Launchpad:

[https://bugs.launchpad.net/snapstore-snap](https://bugs.launchpad.net/snapstore-snap)


### Known issues

1. The `snap download` command doesn't do the download of the snap through
   snapd service, and therefore doesn't know about the Snap Store Proxy
   and will try to fetch the snap directly. [Forum
   thread](https://forum.snapcraft.io/t/improvements-in-snap-download/1422)
2. Need to be root when configuring the snap proxy.
   [Forum thread](https://forum.snapcraft.io/t/should-snapctl-set-in-apps-trigger-the-configure-hook/2032/7)
