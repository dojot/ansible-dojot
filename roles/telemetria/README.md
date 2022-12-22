# Telemetry

## About

This readme contains the necessary steps to deploy [`Grafana`](https://grafana.com/grafana/) for telemetry using keycloak for authentication

## Disclaimer

With a focus on improving the service, aiming at greater maintainability and programmability of the solution. We started a refactoring of the service using [`Helm`](https://helm.sh/), initially we are porting grafana and then we will porte all the rest of the observability solution.

## How to view and access data in grafana?

* If the balancer is already being used in the cluster, grafana has a mapped port: ``8088``. So just access the browser with the balancer IP and the mentioned port to access grafana.

http://<ip-balancer>:8088

Example:

http://196.10.100.103:8088

## How to deploy Telemetry solution?

Initially, it is necessary to set ```telemetry``` variable to ``true`` in the ``services.yaml`` file (`inventories/example_local/group_vars/all/services.yaml`). After that just run the playbooks below:

```
ansible-playbook -K -k -u dojot -i inventories/example_local/ volume.yaml -t telemetria
```

And:

```
ansible-playbook -K -k -u dojot -i inventories/example_local/ deploy.yaml -t telemetria
```

# How to use Grafana with Keycloak

The first step is to access keycloak and create a ``user``.

Note: The username and email fields are mandatory when adding a new user.

Note 2: The email can be generic, for example, project@123, user@user and etc.

* Set a password: The password needs to be at least 8 characters long, with at least one:
    - uppercase character.
    - special character.
    - number character.

* Define in Role Mappings the visibility for your user, between: Admin, Editor or Viewer.

The environment variables must be modified if a client other than grafana is included and if a secret is created.

* client_id -> Customer name created in Keycloak. Ex: grafana

* client_secret -> We left this variable blank so that it is not necessary to start the whole system and then have to restart the telemetry deployment to include the secret but we left the variable because it is necessary for grafana.ini and also to provide more security options. Ex: mTl2HE6l1qXxNDoW5mMvepFOQhOCelCV
