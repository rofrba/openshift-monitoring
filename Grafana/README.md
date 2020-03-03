## Grafana

### IMPORTANT: First check if Monitoring project and Prometheus are installed. If they aren't installed, verify the [Prometheus Installation](../Prometheus)

#### Edit [grafana.ini](ConfigMaps/grafana.ini) to set credentials for admin user 

#### Edit [datasources.yaml](Secrets/datasources.yaml) to set the prometheus datasource. It's recommended to use the service to connect.

#### Create the necessary resources

`oc create configmap  grafana-dashboards  --from-file=dashboards.yml  -n new-project-monitoring`

`oc create configmap  grafana-config  --from-file=grafana.ini  -n new-project-monitoring `

`oc create -f datasources.yaml -n new-project-monitoring`

#### OPTIONAL: If you need mount particular static dashboards, use this path: /grafana-dashboard-definitions/0/dashboard-name

#### Create a new-app based on [template](template.yaml)

`oc new-app -f template.yaml`


