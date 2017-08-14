# Support Hypercontainer in OpenStack Zun

## Main idea

As mentioned in Zun architecture decisions [etherpad](https://etherpad.openstack.org/p/zun-architecture-decisions),
`Zun wants to support container runtimes, such as docker, hypercontainer & rkt container.`.
Docker is already supported, but hypercontainer isn't. This note describes the way to implement
HyperContainer supporting.

## What is HyperContainer?

HyperContainer is a hypervisor-agnostic technology that allows you to run
Docker images on plain hyper.

**Advantages**:

- Fast as Container.
- Isolated by VM.
- Pod in First class.
- Immutable Infrastructure.

[Source code](https://github.com/hyperhq/hyperd)

[Documentation](https://docs.hypercontainer.io)

## Work items

1. Develope a HyperContainer python client a.k.a *hyperctn-py*. We can ref [docker-py](https://github.com/docker/docker-py), [hyper REST API doc](https://docs.hypercontainer.io/reference/api.html) & [hypernova](https://github.com/hyperhq/hypernova/)

2. Upload hyperctn-py to PyPi then we can install it via pip.

3. Use hyperctn-py, create hypercontainer driver (container, image).

