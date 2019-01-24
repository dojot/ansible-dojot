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

* *dojot_kubeconfig_file_path*: Path to the kubeconfig file that will be used to access the kubernetes API endpoints. If not set will use the default environment that is accessible by the node
* *dojot_kubernetes_rbac*: This variable controls the creation of RBAC rules for dojot. Default value is **true**
* *dojot_booststrap*: Defines if packages required for the deployment should be installed. Defaults to **true**

### - Zookeeper

* *dojot_zk_client_port*: Port exposed by Zookeeper for client access. Defaults to **2181**.
* *dojot_zk_server_port*: Port exposed by Zookeeper for server access. Defaults to **2888**
* *dojot_zk_election_port*: Port exposed by zookeeper for cluster election. Defaults to **3888**
* *dojot_zk_cluster_size*: Inital cluster size for deploying zookeeper. Defaults to **1**.
* *dojot_zk_persistent_volumes*: Defines whether ot not the zookeeper services will use persistent volumes, this should be supported by the kubernetes setup. Defaults to **true**
* *dojot_zk_volume_size*: Size of the persistent volume created for the zookeeper service. Defaults to **3G**

### - PostgreSQL

* *dojot_psql_default_db*: Name of the default database created by postgres. Defaults to **postgres**
* *dojot_psql_super_user*: Name of the postgreSQL super user. Defaults to postgres.
* *dojot_psql_super_passwd*: Password for the PostgreSQL super user. Defaults to postgres
* *dojot_psql_version*: Version of the PostgreSQL container '*postgresql*' used on this deployment. Defaults to **9.6.11-alpine**
* *dojot_psql_kong_user*: Username for accessing the kong database. Defaults to **kong**
* *dojot_psql_kong_passwd*: Password for accessing the kong database. Defaults to **kong**
* *dojot_psql_kong_db*: Name of the database created to be used by the kong service. Defaults to **kong**
* *dojot_psql_auth_user*: Username for accessing the auth database. Defaults to **auth**
* *dojot_psql_auth_passwd*: Password for accessing the auth database. Defaults to **auth**
* *dojot_psql_devm_user*: Username for accessing the devm database. Defaults to **devm**
* *dojot_psql_devm_passwd*: Password for accessing the devm database. Defaults to **devm**
* *dojot_psql_port*: PostgreSQL port configured for acessing the database by the dojot services. Defaults to **5432**
* *dojot_psql_persistent_volumes*: If persistent volumes are not supported by your environment this variable should be set to false. Defaults to **true**
* *dojot_psql_volume_size*: Size of the persistent volume that will be created for the PostgreSQL volume. Defaults to **10G**

### - MongoDB

* *dojot_mongodb_super_user*: Super user name for accessing MongoDB. Defaults to **mongodb**
* *dojot_mongodb_super_passwd*: Super user password for accessing MongoDB. Defaults to **mongodb**
* *dojot_mongodb_version*: Container version for the mongodb container. Defaults to **3.4**
* *dojot_mongodb_port*: MongoDB access port. Defaults to **27017**
* *dojot_mongodb_persistent_volumes*: If persistent volumes are not supported by your environment this variable should be set to false. Defaults to **true**
* *dojot_mongodb_volume_size*: Size of the persistent volume that will be created for the mongoDB volume. Defaults to **30G**

### - API Gateway

* *dojot_internal_http_port*: Defines the internal port that will be exposed for http traffic by the Kong service. Defaults to **8000**
* *dojot_internal_api_config_port*: Defines the internal port for kong administration tasks. Defaults to **8001**
* *dojot_apigw_version*: Version of the api gateway container 'dojot/kong' used by this deployment. Default value **v0.2.1-static**

### - Auth

* *dojot_auth_email_enabled*: This configuration enables auth to send emails to users when a new account is created, enabling this requires email parameters to be set. Defaults to: **false**
* *dojot_auth_email_host*: SMTP email server associated with the account that sends the registration e-mail.
* *dojot_auth_email_user*: E-Mail account used as sender of the registration e-mail for new users.
* *dojot_auth_email_passwd*: Access password for the e-mail account.

### - Device Manager

* *dojot_devm_crypto_pass*: Cryptography Password configuration for the device manager. Defaults to **dojotdojot**
* *dojot_devm_crypto_iv*: Cryptography IV configurations for the device manager. Defaults to **"1234567890123456"**
* *dojot_devm_crypto_salt*: Cryptography salt for the device manager. Defaults to **dojot**

### - Kafka

* *dojot_kafka_port*: Kafka port exposed to the services. Defaults to **9092**
* *dojot_kafka_cluster_size*: Number of nodes inittialy present on the deployment. Defaults to **1**
* *dojot_kafka_persistent_volumes*: Configures whether kafka should use persistent volumes or not, must be supported by the environment. Defaults to **false**
* *dojot_kafka_volume_size*: Size of the Kafka volumes that are created. Defaults to **10Gi**

### - RabbitMQ

* *dojot_rabbitmq_version*: Version of the RabbitMQ container used on this deployment. Defaults to **3.7-alpine**
