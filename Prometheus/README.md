## Prometheus

### This is an example to install Prometheus to monitor another different endpoint from the Openshift-Monitoring project.

#### Create a new project into OCP

`oc new-project  new-project-monitoring`

#### Edit [prometheus.yml](ConfigMaps/prometheus.yml) to set the endpoints connections

#### Create a new-app based on [template](template.yaml)

`oc new-app -f template.yaml`

#### OPTIONAL: You can add PV for persist metrics. Mount the PV on path  /prometheus



