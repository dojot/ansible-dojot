# Telemetry

## About

This readme contains the necessary steps to deploy  [`Grafana`](https://grafana.com/grafana/) for telemetry using keyclock for authentication

## Disclaimer

With a focus on improving the service, aiming at greater maintainability and programmability of the solution. We started a refactoring of the service using [`Helm`](https://helm.sh/), initially we are porting grafana and then we will porte all the rest of the observability solution.

As the inclusion of services (Prometheus, Loki, Promtail and Grafana) is under development, some services are currently not being monitored. The following describes the services already implemented.

## How to view and access data in grafana?

* If the balancer is already being used in the cluster, grafana has a port configured ``30009``. So just access the browser with the balancer IP and the mentioned port to access grafana.

http://<ip-balancer>:30009

Example:

http://196.10.100.103:30009

## How to deploy Telemetry solution?

Initially, it is necessary to enable the ```telemetry``` option with ``true`` in the ``services.yaml`` file and after that just run the commands below:

```
ansible-playbook -K -k -u dojot -i inventories/example_local/ volume.yaml
```

And:

```
ansible-playbook -K -k -u dojot -i inventories/example_local/ deploy-monitoring.yaml
```

# How to use Grafana with Keycloak

The first step is to access keycloak and create a ``client``. Then in the users section it is necessary to add a new group to create and add users.

Note: The username and email fields are mandatory when adding a new user.

Note 2: The email can be generic, for example, project@123, user@user and etc.

The environment variables must be filled after the client and users are included in the Keycloak for the deployment to be carried out:

* client_id -> Customer name created in Keycloak. Ex: grafana

* client_secret -> Secret generated after creating the client. Ex: mTl2HE6l1qXxNDoW5mMvepFOQhOCelCV

* group_keyclock -> Group that can be created to include users. Ex: grafana

* group_visibility -> User visibility can be, Admin, Viewer or Editor. Ex: Admin
