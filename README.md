# ansible-dojot

![dojot Logo](https://avatars0.githubusercontent.com/u/31219238?s=80&v=4)

Deploy dojot on Kubernetes using Ansible

## Description

This module is responsible for deploying the dojot service and dependencies to a Kubernetes cluster.

It contain playbooks that execute the deployment based on the inventory file where the kubernetes node informations, access parameters and dojot configuration is defined.

## Module Requirements

This module requires:

* Ansible > 2.6

To install the requirements run the following command:

```bash
pip install -r requirements.txt
```

## Deploy Requirements

To deploy dojot it is required an environment of at least one node of Kubernetes with access to docker hub in order to download the components containers.

It is necessary a kubeconfig file containing access and authorization information for this kubernetes environment.

The minimal Kubernetes version support is Kubernetes **v1.11**.

If persistent storage is required, it is expected that a Storage Class named dojot exists with a proper storage backend previously configured and working with the K8s environment.

## Inventory Configuration

The inventory configuration that is required for using the deployment playbook is:

* The list of nodes that are part of the K8s cluster groupped as: dojot-k8s where the first of this nodes will be used to call the K8s API
* Obligatory configuration variables for the dojot deployment associated with the group
* Optional variables for environment customization

There is an example inventory defined in this repository that can be used as reference on the folder *inventories/example*.

Variables definition and default values are explained further down on this document.

## Deployment Steps

The steps required for executing the deployment playbook are defined below:

1. bla
2. bleh
3. bli
4. bló
5. bluh
6. blão

## Inventory Variables

A reference of the variables that have to be set on the inventory
is found on the document:

[Inventory Variables](docs/vars.md)

## License

GPLv3

## Copyright

Author: Eric Baum

Copyright 2018, CPqD