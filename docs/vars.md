# Inventory variables

This document exposes which variables should be set on the inventory
before deploying dojot

## Mandatory Variables

* *dojot_namespace*: Defines the namespace where dojot will be deployed
* *dojot_version*: Sets the dojot version that will be used for all the modules
* *dojot_domain_name*: Defines the domain name for the dojot infrastructure
* *dojot_storage_class_name*: Defines the name of the storage class used by the dojot volumes

## Optional Variables

### - Dojot

* *dojot_kubeconfig_file_path*: Path to the kubeconfig file that will be used to
 access the kubernetes API endpoints. If not set will use the default
 environment that is accessible by the node

* *dojot_kubernetes_rbac*: This variable controls the creation of RBAC
 rules for dojot. Default value is **true**

### - Zookeeper

<!-- TODO: Add zk variables -->

### - PostgreSQL

* *dojot_psql_super_user*: Name of the postgreSQL super user.
 Defaults to postgres.

* *dojot_psql_super_passwd*: Password for the PostgreSQL super user.
 Defaults to postgres