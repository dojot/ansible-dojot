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

Initially, it is necessary to enable the ````telemetry``` option with ``true`` in the ``services.yaml`` file and after that just run the commands below:

```
ansible-playbook -K -k -u dojot -i inventories/example_local/ volume.yaml
```

And:

```
ansible-playbook -K -k -u dojot -i inventories/example_local/ deploy-monitoring.yaml
```

# User and password to access grafana

**User**: ``admin``

**Password**: ``admin``