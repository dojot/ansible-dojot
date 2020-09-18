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

* Install the requirements:

```bash
pip install -r requirements.txt
```

* Create an inventory folder for your setup or copy an example inventory

```bash
mkdir -p inventories/SETUP_NAME
```

or

```bash
cp -r inventories/example_local inventories/SETUP_NAME
```

* Fill up the hosts.yaml file with the nodes that compose the environment, the kubernetes nodes should be added to the groups dojot-k8s

* Set the variables with proper values for the deployment, default values and the meaning of each variable is defined on the variables file

* Run the ansible-playbook to proceed with the deployment

```bash
ansible-playbook -K -i inventories/SETUP_NAME deploy.yaml
```

* The dojot services are acessible on the Node Ports that were set by Kubernetes, to verify what ports are configured, execute:

```bash
kubectl get service -n dojot kong iotagent-mosca
```

## Inventory Variables

A reference of the variables that have to be set on the inventory
is found on the document:

[Inventory Variables](docs/vars.md)

## Scripts

In the [scripts folder](./scripts) you can find the `up` and `down` scripts. You can use them to
bring up the project and to remove all brought up services, respectively. You can check out their
help by passing the `-h` flag.

## License

GPLv3

## Copyright

Author: Eric Baum

Copyright 2019, CPqD
