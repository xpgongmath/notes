# Failed to handle shared network scenario

> Bugs: https://bugs.launchpad.net/zun/+bug/1727910

Network (shared) without subnetpool
Kuryr-libnetwork create subnetpool ---> project\_id

## Reproduce
```
$ source /opt/stack/devstack/openrc admin admin
$ openstack network create --share test
$ openstack subnet create --subnet-range 10.2.0.0/24 --network test testsubnet
$ zun run --net network=test nginx
$ source /opt/stack/devstack/openrc demo demo
$ zun run --net network=test nginx
$ zun show cdfa61e6-3764-4f47-ac11-8ea54a4394e6
...
| status | Error
| status_reason | Docker internal error: 500 Server Error: Internal Server Error ("IpamDriver.RequestPool: Another pool with same cidr exist. ipam and network options not used to pass pool name").
```

## Problem:

- testsubnet does not have subnetpool -> kuryr-libnetwork will create a new one (kuryrPool-10.2.0.0/24) with project_id = admin project id.
- 2nd time trying to run a container with network test. In Zun side, it can't get subnetpool id (In demo project, subnet & subnetpool is in admin project).
- Without passing pool id & pool name, kuryr-libnetwork will try to create a new kuryrPool. But firstly, it will get subnet pool with name & pool_cidr. It will return subnetpool kuryrPool-10.2.0.0/24 -> raise Exception.