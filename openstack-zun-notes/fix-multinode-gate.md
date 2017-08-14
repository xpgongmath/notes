# Fix OpenStack Zun multinode gate

## Problems.

Tempest test is failed because some tests raise Docker internal error [check
the log](http://logs.openstack.org/19/485419/16/check/gate-tempest-dsvm-zun-multinode-docker-sql-ubuntu-xenial-nv/a3f66a7/logs/screen-zun-compute.txt.gz#_Jul_28_19_04_37_665901)

[Tempest log](http://logs.openstack.org/19/485419/16/check/gate-tempest-dsvm-zun-multinode-docker-sql-ubuntu-xenial-nv/a3f66a7/logs/tempest.txt.gz?level=ERROR)

## The solution?

1. [The defined bug #1690284](https://bugs.launchpad.net/zun/+bug/1690284)

2. #TBD
