## Grafana

### IMPORTANT: First check if Monitoring project and Prometheus are installed. If they aren't installed, verify the [Prometheus Installation](../Prometheus)

#### Edit [grafana.ini](ConfigMaps/grafana.ini) to set credentials for admin user 

#### Edit [datasources.yaml](Secrets/datasources.yaml) to set the prometheus datasource. It's recommended to use the service to connect.


#### Create a new-app based on [template](template.yaml)

`oc new-app -f template.yaml`

#### OPTIONAL: If you need mount particular static dashboards, use this path: /grafana-dashboard-definitions/0/dashboard-name

