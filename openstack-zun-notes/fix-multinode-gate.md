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

------------------------------------------------------------------------------------

> NOTE (07/09/2017): The previous error raised because DOCKER_CLUSTER_STORE -> HOST\_API.
Set to SERVICE\_HOST. Problem is solved.

> Still exists another problem:

    self.assertEqual('Running', self._get_container_state(model.uuid))

    --> _get_container_state will use docker.client() to get_container() in
    localhost. With container which is created in another host --> None.

The approach: http://paste.ubuntu.com/25482987/
