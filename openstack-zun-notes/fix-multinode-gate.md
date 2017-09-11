# Fix OpenStack Zun multinode gate

## Problems.

Tempest test is failed because some tests raise Docker internal error [check
the log](http://logs.openstack.org/19/485419/16/check/gate-tempest-dsvm-zun-multinode-docker-sql-ubuntu-xenial-nv/a3f66a7/logs/screen-zun-compute.txt.gz#_Jul_28_19_04_37_665901)

[Tempest log](http://logs.openstack.org/19/485419/16/check/gate-tempest-dsvm-zun-multinode-docker-sql-ubuntu-xenial-nv/a3f66a7/logs/tempest.txt.gz?level=ERROR)

## The solution?

1. [The defined bug #1690284](https://bugs.launchpad.net/zun/+bug/1690284)

2. #TBD

Etherpad: https://etherpad.openstack.org/p/zun-multihost-problems

Related bp: https://blueprints.launchpad.net/kuryr-libnetwork/+spec/existing-subnet


> 09/09/2017

Figure out the problem but unable to test it [1]. The gate failed because of some
strange reason [2]. Exit code 137 - Running out of memory.

[1] https://review.openstack.org/#/c/501651/
[2]
http://logs.openstack.org/51/501651/10/experimental/gate-tempest-dsvm-zun-multinode-docker-sql-ubuntu-xenial-nv/b7b364a/console.html#_2017-09-09_03\_10\_01\_463016
