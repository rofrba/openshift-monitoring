## Prometheus

### This is an example to install Prometheus to monitor another different endpoint from the Openshift-Monitoring project.

#### Create a new project into OCP

`oc new-project  new-project-monitoring`

#### Import Image from Red Hat Registry

`oc import-image openshift/prometheus:v3.11.170-5 --from=registry.redhat.io/openshift3/prometheus:v3.11.170-5 --confirm -n openshift`

#### Edit [template.yaml](template.yaml) to set the endpoints connections in the ConfigMap section

#### Create a new-app based on template

`oc new-app -f template.yaml`

#### OPTIONAL: You can add PV for persist metrics. In this case, mount the PV on path  /prometheus



