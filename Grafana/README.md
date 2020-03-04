## Grafana

### IMPORTANT: First check if Monitoring project or Prometheus are installed. If they aren't installed, verify the [Prometheus Installation](../Prometheus)

#### Import Image for Red Hat Registry

`oc import-image openshift/grafana:v3.11 --from=registry.redhat.io/openshift3/grafana:v3.11 --confirm -n openshift`

#### Edit [template.yaml](template.yaml) to set credentials for admin user in the section _ConfigMap/grafana.ini_ and edit the same template for set the prometuehs datasoruce in the section _ConfigMap/datasources.yaml (It's recommended to use the service to connect)_ 


#### Create a new-app based on [template](template.yaml)

`oc new-app -f template.yaml`

#### OPTIONAL: If you need mount particular static dashboards, use this path: /grafana-dashboard-definitions/0/dashboard-name

