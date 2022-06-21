# Inventory variables

This document exposes which variables should be set on the inventory
before deploying dojot

## Mandatory Variables

* *dojot_namespace*: Defines the namespace where dojot will be deployed.
* *dojot_backend_version*: Sets the dojot version that will be used for backend modules.
* *dojot_frontend_version*: Sets the dojot version that will be used for frontend modules.
* *dojot_domain_name*: Defines the domain name for the dojot infrastructure.
* *dojot_storage_class_name*: Defines the name of the storage class used by the dojot volumes **(local-storage or nfs)**.

## Optional Variables

### - Dojot

* *dojot_kubeconfig_file_path*: Path to the kubeconfig file that will be used to access the kubernetes API endpoints. If not set will use the default environment that is accessible by the node.
* *dojot_kubernetes_rbac*: This variable controls the creation of RBAC rules for dojot. Default value is **true**.
* *dojot_booststrap*: Defines if packages required for the deployment should be installed. Defaults to **true**.

* *dojot_vernemq_replicas*: Set number of replicas for VerneMQ. Defaults to **1**.
* *dojot_vernemq_max_replicas*: Set number max of replicas for VerneMQ. Defaults to **30**.
* *dojot_bridges_replicas*: Set number of replicas for K2V, V2K and Loopback, and also modifies the number of partitions in Kafka topics. Defaults to **1**.
* *dojot_v2k_max_replicas*: Set number max of replicas for V2K. Defaults to **21**.
* *dojot_k2v_max_replicas*: Set number max of replicas for K2V. Defaults to **21**.
* *value_metric_trigger_cpu*: Keda HPA cpu usage metric trigger. Defaults to **80**.
* *dojot_fixed_nodeports_enabled*: Set whether dojot's nodeport services will be fixed. Defaults to **false**.
* *dojot_nodeports*: Range of fixed ports for dojot services with external access.
* *dojot_enable_node_affinity*: Enables node affinity for all services. Beware that you must configure your nodes to match the labels in the files. Default to **false**.
* *dojot_dojot_nodenames*: List of workers nodenames that will be labled with the dojot label.
* *dojot_kafka_nodenames*: List of workers nodenames that will be labled with the kafka label.
* *dojot_x509_nodenames*: List of workers nodenames that will be labled with the x509 label.
* *dojot_vernemq_nodenames*: List of workers nodenames that will be labled with the vernemq label.
* *nfs_server_node*: NFS server nodename.

* *dojot_volume_directory*: Defines the base path where volumes will be mapped. Inform local volume path or mount volume. Defaults to **/mnt/data**

* *dojot_enable_https_nginx*: Active HTTPS in NGINX. If enable_https_nginx = true, is necessary IP public and domain in NGINX server. Defaults to **false**
* *dojot_certbot_admin_email*: Certbot admin email.
* *dojot_certbot_certs_domain*: Certbot certs domain


### - Zookeeper

* *dojot_zk_client_port*: Port exposed by Zookeeper for client access. Defaults to **2181**.
* *dojot_zk_server_port*: Port exposed by Zookeeper for server access. Defaults to **2888**.
* *dojot_zk_election_port*: Port exposed by Zookeeper for cluster election. Defaults to **3888**.
* *dojot_zk_cluster_size*: Inital cluster size for deploying Zookeeper. Defaults to **1**.
* *dojot_zk_volume_size*: Size of the persistent volume created for the Zookeeper service. Defaults to **1G**.

### - PostgreSQL

* *dojot_psql_default_db*: Name of the default database created by postgres. Defaults to **postgres**.
* *dojot_psql_super_user*: Name of the postgreSQL super user. Defaults to **postgres**.
* *dojot_psql_super_passwd*: Password for the PostgreSQL super user. Defaults to **postgres**.
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
* *dojot_psql_volume_size*: Size of the persistent volume that will be created for the PostgreSQL volume. Defaults to **2G**.


### - MongoDB

* *dojot_mongodb_super_user*: Super user name for accessing MongoDB. Defaults to **mongodb**.
* *dojot_mongodb_super_passwd*: Super user password for accessing MongoDB. Defaults to **mongodb**.
* *dojot_mongodb_version*: Container version for the mongodb container. Defaults to **3.4**.
* *dojot_mongodb_port*: MongoDB access port. Defaults to **27017**.
* *dojot_mongodb_volume_size*: Size of the persistent volume that will be created for the mongoDB volume. Defaults to **2G**.

### - API Gateway

* *dojot_internal_http_port*: Defines the internal port that will be exposed for HTTP traffic by the Kong service. Defaults to **8000**.
* *dojot_internal_https_port*: Defines the internal port that will be exposed for HTTPS traffic by the Kong service. Defaults to **8443**.
* *dojot_internal_api_config_port*: Defines the internal port for Kong administration tasks. Defaults to **8001**.
* *dojot_apigw_version*: Version of the api gateway container 'dojot/kong' used by this deployment. Default value **v0.2.1-static**.
* *dojot_apigw_volume_size*: Size of the persistent volume that will be created for Kong certificates directory. Defaults to **5Mi**.
* *dojot_apigw_enable_mutual_tls*: Enables mutual TLS communication. You must enable Kong volumes if this is true. Defaults to **false**.

### - Auth

* *dojot_auth_email_enabled*: This configuration enables auth to send emails to users when a new account is created, enabling this requires email parameters to be set. Defaults to: **false**.
* *dojot_auth_email_host*: SMTP email server associated with the account that sends the registration e-mail.
* *dojot_auth_email_user*: E-Mail account used as sender of the registration e-mail for new users.
* *dojot_auth_email_passwd*: Access password for the e-mail account.
* *dojot_auth_version*: Version of the auth container. Defaults to **dojot_backend_version**.

### - Device Manager

* *dojot_devm_crypto_pass*: Cryptography Password configuration for the device manager. Defaults to **dojotdojot**.
* *dojot_devm_crypto_iv*: Cryptography IV configurations for the device manager. Defaults to **"1234567890123456"**.
* *dojot_devm_crypto_salt*: Cryptography salt for the device manager. Defaults to **dojot**.
* *dojot_devm_version*: Version of the device manager container. Defaults to **dojot_backend_version**.

### - Kafka

* *dojot_kafka_port*: Kafka port exposed to the services. Defaults to **9092**.
* *dojot_kafka_cluster_size*: Number of nodes inittialy present on the deployment. Defaults to **1**.
* *dojot_kafka_volume_size*: Size of the Kafka volumes that are created. Defaults to **2Gi**.

### - RabbitMQ

* *dojot_rabbitmq_version*: Version of the RabbitMQ container used on this deployment. Defaults to **3.7-alpine**.

### - Flowbroker

* *dojot_flowbroker_version*: Version of the flowbroker container. Defaults to **dojot_backend_version**.
* *dojot_flowbroker_context_manager_version*: Version of the context manager container. Defaults to **dojot_backend_version**.

### - GUI

* *dojot_gui_version*: Version of the GUI container. Defaults to **dojot_frontend_version**.

### - GUI V2

* *dojot_guiv2_enabled*: Defines whether the GUI V2 will be deployed or not. Defaults to **false**.
* *dojot_guiv2_version*: Version of the GUI V2 container. Defaults to **dojot_frontend_version**.
* *dojot_guiv2_image*: Image to be used in GUI V2 deployment. Defaults to **dojot/gui-v2**.

### - History

* *dojot_history_version*: Version of the history container. Defaults to **dojot_backend_version**.

### - IoTAgent Mosca

* *dojot_iotagent_mosca_version*: Version of the IoT Agent Mosca container. Defaults to **dojot_backend_version**.
* *dojot_insecure_mqtt*: Defines wheter or not the agent accepts insecure mqtt connections. Defaults to **true**.

### - Persister

* *dojot_persister_version*: Version of the persister container. Defaults to **dojot_backend_version**.

### - x509 Identity Management

* *dojot_x509_identity_management_volume_size*: Size of the x509 Identity Management volumes that are created. Defaults to **10Mi**.
* *dojot_psql_ejbca_user*: EJBCA PostgreSQL database user. Defaults to **ejbca**.
* *dojot_psql_ejbca_passwd*: EJBCA PostgreSQL database password. Defaults to **ejbca**.
* *dojot_x509_identity_mgmt_version*: Version of the x509 Identity Management container. Defaults to **dojot_backend_version**.
* *dojot_x509_identity_mgmt_replicas*: Number of replicas. Beware that you must configure a volume if you want more than one instance. Defaults to **1**.
* *dojot_x509_ejbca_version*: Version of the x509 EJBCA container. Defaults to **dojot_backend_version**.
* *dojot_x509_ejbca_replicas*: Number of replicas. Beware that you must configure a volume if you want more than one instance. Defaults to **1**.

### - Kafka Loopback

* *dojot_loopback_version*: Version of the Kafka loopback container. Defaults to **dojot_backend_version**.

### - Dojot InfluxDB

* *dojot_influxdb_version*: InfluxDB container version. Defaults to **v2.0.2**.
* *dojot_influxdb_port*: Port that will be used to communicate with InfluxDB. Defaults to **8086**.
* *dojot_influxdb_user*: InfluxDB admin user. Defaults to **8086**.
* *dojot_influxdb_token*: InfluxDB admin token. Defaults to **dojot@token_default**.
* *dojot_influxdb_passwd*: InfluxDB admin password. Defaults to **dojot@password**.
* *dojot_influxdb_organization_name*: InfluxDB organization name. Defaults to **admin**.
* *dojot_influxdb_bucket*: InfluxDB bucket name. Defaults to **devices**.
* *dojot_influxdb_retention*: InfluxDB data retention period for *dojot_influxdb_organization_name*, for other retentions it is necessary to use an environment variable in the influxdb-storer. Valid units are nanoseconds (ns), microseconds (us or µs), milliseconds (ms), seconds (s), minutes (m), hours (h), days (d),  weeks (w) and 0 is infinite retention. It is considered only the first time that InfluxDB is started. Defaults to **7d**.
* *dojot_influxdb_volume_size*: Size of the InfluxDB volumes that are created. Defaults to **2Gi**.


### - Dojot InfluxDB Storer

* *dojot_influxdb_storer_version*: InfluxDB Storer container version. Defaults to **dojot_backend_version**.
* *dojot_influxdb_storer_log_level*: InfluxDB Storer log level. Defaults to **info**.


### - Dojot InfluxDB Retriever

* *dojot_influxdb_retriever_version*: InfluxDB Retriever container version. Defaults to **dojot_backend_version**.
* *dojot_influxdb_retriever_log_level*: InfluxDB Retriever log level. Defaults to **info**.


### - Kafka WS

* *dojot_kafka_ws_version*: Version of the Kafka WS container. Defaults to **dojot_backend_version**.
* *dojot_kafka_ws_volume_size*: Size of the Kafka WS volumes that are created. Defaults to **5Mi**.
* *dojot_kafka_port*: Port that will be used to communicate with Kafka. Defaults to **9092**.
* *dojot_kafka_ws_port*: Port that will be used by the Kafka WS service. Defaults to **8080**.
* *dojot_kafka_ws_redis_port*: Port that will be used to communicate with Redis. Defaults to **6379**.
* *dojot_kafka_ws_enable_tls*: Activates the TLS communication. Defaults to **false**.
* *dojot_kafka_ws_ticket_secret*: Kafka WS secret that should be unique for each environment.

### - Certificate ACL

* *dojot_certificate_acl_version*: Version of the Certificate ACL container. Defaults to **dojot_backend_version**.
* *dojot_certificate_acl_volume_size*: Size of the Certificate ACL volumes that are created. Defaults to **5Mi**.
* *dojot_certificate_acl_redis_port*: Port that will be used to communicate with Redis. Defaults to **6379**.
* *dojot_kafka_port*: Port that will be used to communicate with Kafka. Defaults to **9092**.

### - HTTP Agent

* *dojot_http_agent_version*: Version of the HTTP Agent container. Defaults to **dojot_backend_version**.
* *dojot_http_agent_port*: Port that will be used to communicate with HTTP Agent. Defaults to **8080**.
* *dojot_kafka_port*: Port that will be used to communicate with Kafka. Defaults to **9092**.

### - File MGMT

* *dojot_file_mgmt_version*: Version of the File MGMT container. Defaults to **dojot_backend_version**.
* *dojot_kafka_port*: Port that will be used to communicate with Kafka. Defaults to **9092**.
* *dojot_minio_files_access_key*: MinIO access key.
* *dojot_minio_files_secret_key*: MinIO secret key.
* *dojot_minio_files_volume_size*: Size of the File Mgmt volumes that are created. Defaults to **2Gi**.
* *dojot_minio_bucket_suffix*: MinIO bucket suffix of the File Mgmt. Defaults to **cpqd.dojot**.


### - MinIO Files

* *dojot_minio_files_access_key*: MinIO access key.
* *dojot_minio_files_secret_key*: MinIO secret key.
* *dojot_minio_files_version*: Version of the MinIO.
* *dojot_minio_files_api_port*: API Port of the MinIO. Defaults to **9000**.
* *dojot_minio_files_cluster_size*: Size of the MinIO Files cluster. Defaults to **1**.
* *dojot_minio_files_volume_size*: Size of the MinIO Files volumes that are created. Defaults to **2Gi**.

### - Metrics and Logging

* *dojot_enable_locust_exporter*: Whether to activate the Locust Exporter or not. Defaults to **false**.
* *dojot_locust_exporter.ip*: IP or hostname where there is a Locust Exporter running. Defaults to **127.0.0.1**.
* *dojot_locust_exporter.port*: Port exposed by Locust Exporter. Defaults to **9646**.
* *dojot_monitoring_namespace*: Namespace that will be created for monitoring stack deployment. Defaults to **dojot-monitoring**.
* *dojot_helm_install*: Whether to install helm3 binary or not. Defaults to **true**.
* *dojot_helm_version*: Helm version number. Defaults to **3.7.2**.
* *dojot_helm_os*: The OS of the Helm redistributable. Defaults to **linux**.
* *dojot_helm_architecture*: The CPU architecture of the Helm executable to install. Defaults to *amd64*.
* *dojot_helm_mirror*: Mirror to download Helm from. Defaults to **https://get.helm.sh**.
* *dojot_helm_install_dir*: Directory where Helm should be installed. Defaults to **/usr/local/share/helm**.

### - Kubernetes Cluster

* *k8s_version*: Version of the Kubernetes cluster. Defaults to **1.17.3-00**.
* *docker_log_size*: The maximum size of the log before it is rolled. Defaults to **20m**.
* *docker_log_files_amount*: The maximum amount of log files before it is rolled. Defaults to **5**.

### - HAProxy

* *haproxy_version*: Version of the HAProxy service. Defaults to **2.0**.

### - NGINX

* *nginx_version*: Version of the NGINX service. Defaults to **1.19**.

### - Certbot

* *certbot_auto_renew*: Auto renew Certbot. Defaults to **true**.
* *certbot_auto_renew_user*: Auto renew Certbot User
* *certbot_auto_renew_hour*: Auto renew Certbot Hour. Defaults to **3**.
* *certbot_auto_renew_minute*: Auto renew Certbot Minute. Defaults to **30**.
* *certbot_auto_renew_options*: Auto renew Certbot Options. Defaults to **renew --quiet --webroot -w /data/letsencrypt**.
* *certbot_create_if_missing*: Certbot Option when creating new certs. Defaults to **false**.
* *certbot_create_method*: Certbot certs Method. Defaults to **webroot**.
* *certbot_create_command*: Certbot command.
* *certbot_services*: Certbot service. Defaults to **nginx**.
* *certbot_install_method*: Certbot install method. Defaults to **package**.
* *certbot_repo*: Certbot repo. Defaults to **https://github.com/certbot/certbot.git**.
* *certbot_version*: Certbot version. Defaults to **master**.
* *certbot_keep_updated*: Certbot updated. Defaults to **false**.
* *certbot_package*: Certbot package. Defaults to **letsencrypt**.
* *certbot_dir*: Certbot install directory. Defaults to **/opt/certbot**.

### - Velero Disaster Recovery

* *velero_binary_install*: Whether to install helm3 binary or not. Defaults to **false**.
* *velero_version*: Velero version number. Defaults to *1.7.1*.
* *velero_namespace* Namespace that will be created for velero deployment. Defaults to **velero**.
* *velero_storage_region*: S3URL region. Defaults to `minio`.
* *velero_storage_s3url*: S3URL URL connection. Defaults to `http://minio.minio.svc.cluster.local:9000`.
* *velero_aws_access_key*: S3URL access key (e.g. MINIO_ROOT_USER).
* *velero_aws_secret_key*: S3URL secret key (e.g. MINIO_ROOT_PASSWORD).
* *velero_bucket_name*: S3URL bucket name created to velero. Defaults to `velero`.
* *velero_backup_namespaces*: Backups settings. Defaults to `dojot` and `dojot-monitoring`. See [velero.yaml](../inventories/example_local/group_vars/all/velero.yaml) to more details.
* *velero_prometheus_monitoring*: Whether active the monitoring. Must have Prometheus Operator installed and working. Defaults to `true`.

### - Optional Services

* *optional[influxdb]*: Defines whether InfluxDB will be enabled. Defaults to **false**.
* *optional[influxdb_storer]*: Defines whether InfluxDB Storer service will be enabled. It will only be enabled if InfluxDB is enabled as well. Defaults to **false**.
* *optional[influxdb_retriever]*: Defines whether InfluxDB Retriever service will be enabled. It will only be enabled if InfluxDB is enabled as well. Defaults to **false**.
* *optional[history]*: Defines whether History service will be enabled. Defaults to **true**.
* *optional[persister]*: Defines whether Persister service will be enabled. Defaults to **true**.
* *optional[vernemq]*: Defines whether IotAgent VerneMQ will be enabled. Defaults to **true**.
* *optional[mosca]*: Defines whether IotAgent Mosca will be enabled. It will only be enabled if IotAgent VerneMQ is disabled. Defaults to **false**.
* *optional[lwm2m]*: Defines whether IotAgent Lwm2m will be enabled. Defaults to **false**.
