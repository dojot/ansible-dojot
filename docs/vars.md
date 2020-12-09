# Inventory variables

This document exposes which variables should be set on the inventory
before deploying dojot

## Mandatory Variables

* *dojot_namespace*: Defines the namespace where dojot will be deployed.
* *dojot_version*: Sets the dojot version that will be used for all the modules.
* *dojot_domain_name*: Defines the domain name for the dojot infrastructure.
* *dojot_storage_class_name*: Defines the name of the storage class used by the dojot volumes.

## Optional Variables

### - Dojot

* *dojot_kubeconfig_file_path*: Path to the kubeconfig file that will be used to access the kubernetes API endpoints. If not set will use the default environment that is accessible by the node.
* *dojot_kubernetes_rbac*: This variable controls the creation of RBAC rules for dojot. Default value is **true**.
* *dojot_booststrap*: Defines if packages required for the deployment should be installed. Defaults to **true**.

* *dojot_vernemq_replicas*: Set number of replicas for VerneMQ. Defaults to **1**.
* *dojot_bridges_replicas*: Set number of replicas for K2V, V2K and Loopback, and also modifies the number of partitions in Kafka topics. Defaults to **1**.
* *dojot_fixed_nodeports_enabled*: Set whether dojot's nodeport services will be fixed. Defaults to **false**.
* *dojot_nodeports*: Range of fixed ports for dojot services with external access.
* *dojot_enable_node_affinity*: Enables node affinity for all services. Beware that you must configure your nodes to match the labels in the files. Default to **false**.
* *dojot_node_label.dojot*: Label value for the rest of Dojot components nodes. Defaults to **dojot**.
* *dojot_node_label.kafka*: Label value for Kafka, Zookeeper and Kafka Loopback nodes. Defaults to **kafka**.
* *dojot_node_label.x509*: Label value for x509 nodes. Defaults to **x509**.
* *dojot_node_label.vernemq*: Label value for VerneMQ, K2V and V2K nodes. Defaults to **vernemq**.


### - Zookeeper

* *dojot_zk_client_port*: Port exposed by Zookeeper for client access. Defaults to **2181**.
* *dojot_zk_server_port*: Port exposed by Zookeeper for server access. Defaults to **2888**.
* *dojot_zk_election_port*: Port exposed by Zookeeper for cluster election. Defaults to **3888**.
* *dojot_zk_cluster_size*: Inital cluster size for deploying Zookeeper. Defaults to **1**.
* *dojot_zk_persistent_volumes*: Defines whether ot not the Zookeeper services will use persistent volumes, this should be supported by the kubernetes setup. Defaults to **false**.
* *dojot_zk_volume_size*: Size of the persistent volume created for the Zookeeper service. Defaults to **1G**.

### - PostgreSQL

* *dojot_psql_default_db*: Name of the default database created by postgres. Defaults to **postgres**.
* *dojot_psql_super_user*: Name of the postgreSQL super user. Defaults to postgres.
* *dojot_psql_super_passwd*: Password for the PostgreSQL super user. Defaults to postgres.
* *dojot_psql_version*: Version of the PostgreSQL container '*postgresql*' used on this deployment. Defaults to **9.6.11-alpine**.
* *dojot_psql_kong_user*: Username for accessing the Kong database. Defaults to **kong**.
* *dojot_psql_kong_passwd*: Password for accessing the Kong database. Defaults to **kong**.
* *dojot_psql_kong_db*: Name of the database created to be used by the Kong service. Defaults to **kong**.
* *dojot_psql_ejbca_user*: Username for accessing the EJBCA database. Defaults to **ejbca**.
* *dojot_psql_ejbca_passwd*: Password for accessing the EJBCA database. Defaults to **ejbca**.
* *dojot_psql_ejbca_db*: Name of the database created to be used by the ejbca service. Defaults to **ejbca**.
* *dojot_psql_auth_user*: Username for accessing the auth database. Defaults to **auth**.
* *dojot_psql_auth_passwd*: Password for accessing the auth database. Defaults to **auth**.
* *dojot_psql_devm_user*: Username for accessing the devm database. Defaults to **devm**.
* *dojot_psql_devm_passwd*: Password for accessing the devm database. Defaults to **devm**.
* *dojot_psql_port*: PostgreSQL port configured for acessing the database by the dojot services. Defaults to **5432**.
* *dojot_psql_persistent_volumes*: If persistent volumes are supported by your environment this variable should be set to true. Defaults to **false**.
* *dojot_psql_volume_size*: Size of the persistent volume that will be created for the PostgreSQL volume. Defaults to **2G**.


### - MongoDB

* *dojot_mongodb_super_user*: Super user name for accessing MongoDB. Defaults to **mongodb**.
* *dojot_mongodb_super_passwd*: Super user password for accessing MongoDB. Defaults to **mongodb**.
* *dojot_mongodb_version*: Container version for the mongodb container. Defaults to **3.4**.
* *dojot_mongodb_port*: MongoDB access port. Defaults to **27017**.
* *dojot_mongodb_persistent_volumes*: If persistent volumes are supported by your environment this variable should be set to true. Defaults to **false**.
* *dojot_mongodb_volume_size*: Size of the persistent volume that will be created for the mongoDB volume. Defaults to **2G**.

### - API Gateway

* *dojot_internal_http_port*: Defines the internal port that will be exposed for HTTP traffic by the Kong service. Defaults to **8000**.
* *dojot_internal_https_port*: Defines the internal port that will be exposed for HTTPS traffic by the Kong service. Defaults to **8443**.
* *dojot_internal_api_config_port*: Defines the internal port for Kong administration tasks. Defaults to **8001**.
* *dojot_apigw_version*: Version of the api gateway container 'dojot/kong' used by this deployment. Default value **v0.2.1-static**.
* *dojot_mongodb_persistent_volumes*: Enables the volume for Kong certificates directory, you should configure persistent volumes in your environment for this option to work. Defaults to **false**.
* *dojot_apigw_volume_size*: Size of the persistent volume that will be created for Kong certificates directory. Defaults to **5Mi**.
* *dojot_apigw_enable_mutual_tls*: Enables mutual TLS communication. You must enable Kong volumes if this is true. Defaults to **false**.

### - Auth

* *dojot_auth_email_enabled*: This configuration enables auth to send emails to users when a new account is created, enabling this requires email parameters to be set. Defaults to: **false**.
* *dojot_auth_email_host*: SMTP email server associated with the account that sends the registration e-mail.
* *dojot_auth_email_user*: E-Mail account used as sender of the registration e-mail for new users.
* *dojot_auth_email_passwd*: Access password for the e-mail account.
* *dojot_auth_version*: Version of the auth container. Defaults to **dojot_version**.

### - Device Manager

* *dojot_devm_crypto_pass*: Cryptography Password configuration for the device manager. Defaults to **dojotdojot**.
* *dojot_devm_crypto_iv*: Cryptography IV configurations for the device manager. Defaults to **"1234567890123456"**.
* *dojot_devm_crypto_salt*: Cryptography salt for the device manager. Defaults to **dojot**.
* *dojot_devm_version*: Version of the device manager container. Defaults to **dojot_version**.

### - Kafka

* *dojot_kafka_port*: Kafka port exposed to the services. Defaults to **9092**.
* *dojot_kafka_cluster_size*: Number of nodes inittialy present on the deployment. Defaults to **1**.
* *dojot_kafka_persistent_volumes*: Configures whether Kafka should use persistent volumes or not, must be supported by the environment. Defaults to **false**.
* *dojot_kafka_volume_size*: Size of the Kafka volumes that are created. Defaults to **2Gi**.

### - RabbitMQ

* *dojot_rabbitmq_version*: Version of the RabbitMQ container used on this deployment. Defaults to **3.7-alpine**.

### - Flowbroker

* *dojot_flowbroker_version*: Version of the flowbroker container. Defaults to **dojot_version**.
* *dojot_flowbroker_context_manager_version*: Version of the context manager container. Defaults to **dojot_version**.

### - GUI

* *dojot_gui_version*: Version of the GUI container. Defaults to **dojot_version**.

### - GUI V2

* *dojot_guiv2_enabled*: Defines whether the GUI V2 will be deployed or not. Defaults to **false**.
* *dojot_guiv2_version*: Version of the GUI V2 container. Defaults to **dojot_version**.
* *dojot_guiv2_image*: Image to be used in GUI V2 deployment. Defaults to **dojot/gui-v2**.

### - History

* *dojot_history_version*: Version of the history container. Defaults to **dojot_version**.

### - IoTAgent Mosca

* *dojot_iotagent_mosca_version*: Version of the IoT Agent Mosca container. Defaults to **dojot_version**.
* *dojot_insecure_mqtt*: Defines wheter or not the agent accepts insecure mqtt connections. Defaults to **true**.

### - Persister

* *dojot_persister_version*: Version of the persister container. Defaults to **dojot_version**.

### - x509 Identity Management

* *dojot_x509_identity_mgmt_persistent_volumes*: Configures whether x509 Identity Management should use persistent volumes or not, must be supported by the environment. Defaults to **false**.
* *dojot_x509_identity_management_volume_size*: Size of the x509 Identity Management volumes that are created. Defaults to **10Mi**.
* *dojot_psql_ejbca_user*: EJBCA PostgreSQL database user. Defaults to **ejbca**.
* *dojot_psql_ejbca_passwd*: EJBCA PostgreSQL database password. Defaults to **ejbca**.
* *dojot_x509_identity_mgmt_version*: Version of the x509 Identity Management container. Defaults to **dojot_version**.
* *dojot_x509_identity_mgmt_replicas*: Number of replicas. Beware that you must configure a volume if you want more than one instance. Defaults to **1**.

### - Kafka Loopback

* *dojot_loopback_version*: Version of the Kafka loopback container. Defaults to **dojot_version**.

### - Dojot InfluxDB

* *dojot_influxdb_version*: InfluxDB container version. Defaults to **v2.0.2**.
* *dojot_influxdb_port*: Port that will be used to communicate with InfluxDB. Defaults to **8086**.
* *dojot_influxdb_admin_user*: InfluxDB admin user. Defaults to **8086**.
* *dojot_influxdb_admin_token*: InfluxDB admin token. Defaults to **dojot@token_default**.
* *dojot_influxdb_admin_passwd*: InfluxDB admin password. Defaults to **dojot@password**.
* *dojot_influxdb_organization_name*: InfluxDB organization name. Defaults to **admin**.
* *dojot_influxdb_bucket*: InfluxDB bucket name. Defaults to **devices**.
* *dojot_influxdb_retention*: InfluxDB data retention period. Defaults to **7d**.
* *dojot_influxdb_volume_size*: Size of the InfluxDB volumes that are created. Defaults to **1Gi**.


### - Dojot InfluxDB Storer

* *dojot_influxdb_storer_version*: InfluxDB Storer container version. Defaults to **dojot_version**.
* *dojot_influxdb_storer_log_level*: InfluxDB Storer log level. Defaults to **info**.


### - Dojot InfluxDB Retriever

* *dojot_influxdb_retriever_version*: InfluxDB Retriever container version. Defaults to **dojot_version**.
* *dojot_influxdb_retriever_log_level*: InfluxDB Retriever log level. Defaults to **info**.


### - Kafka WS

* *dojot_kafka_ws_version*: Version of the Kafka WS container. Defaults to **dojot_version**.
* *dojot_kafka_ws_persistent_volumes*: Configures whether Kafka WS should use persistent volumes or not, must be supported by the environment. Defaults to **false**.
* *dojot_kafka_ws_volume_size*: Size of the Kafka WS volumes that are created. Defaults to **5Mi**.
* *dojot_kafka_port*: Port that will be used to communicate with Kafka. Defaults to **9092**.
* *dojot_kafka_ws_port*: Port that will be used by the Kafka WS service. Defaults to **8080**.
* *dojot_kafka_ws_redis_port*: Port that will be used to communicate with Redis. Defaults to **6379**.
* *dojot_kafka_ws_enable_tls*: Activates the TLS communication. Defaults to **false**.
* *dojot_kafka_ws_version*: Version of the Kafka WS container. Defaults to **dojot_version**.
* *dojot_kafka_port*: Port that will be used to communicate with Kafka. Defaults to **9092**.
* *dojot_kafka_ws_port*: Port used to access Kafka WS services. Defaults to **8080**.
* *dojot_kafka_ws_redis_port*: Internally exposed Kafka WS Redis port. Defaults to **6379**.

### - Metrics

* *dojot_enable_locust_exporter*: Whether to activate the Locust Exporter or not. Defaults to **false**.
* *dojot_locust_exporter.ip*: IP or hostname where there is a Locust Exporter running. Defaults to **127.0.0.1**.
* *dojot_locust_exporter.port*: Port exposed by Locust Exporter. Defaults to **9646**.

### - Kubernetes Cluster

* *k8s_version*: Version of the Kubernetes cluster. Defaults to *1.17.3-00*.
* *docker_log_size*: The maximum size of the log before it is rolled. Defaults to *100m*.

### - HAProxy

* *haproxy_version*: Version of the HAProxy service. Defaults to *2.0*.

### - NGINX

* *nginx_version*: Version of the NGINX service. Defaults to *1.19*.
