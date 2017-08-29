# Zun cinder integration

The command:  zun run --mount source=<vol_id>,destination=<path> <image>
(the --mount option can be used multiple times to bind mount multiple volumes)

Patches:

https://review.openstack.org/#/c/473115/
https://review.openstack.org/#/c/491271/
