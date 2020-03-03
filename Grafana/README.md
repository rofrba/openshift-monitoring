## Grafana

### IMPORTANT: First check if Monitoring project and Prometheus are installed. If they aren't installed, verify the [Prometheus Installation](../Prometheus)

`oc import-image openshift/grafana:6.5.2 --from=grafana/grafana:6.5.2 --confirm -n openshift`

`oc new-app -i openshift/grafana:6.5.2  --name grafana -n openshift-metrics `

`oc expose svc/grafana`


[Config Maps mounts](ConfigMaps)


oc create configmap  grafana-dashboards  --from-file=dashboards.yml  -n new-project-monitoring

oc create configmap  grafana-config  --from-file=grafana.ini  -n new-project-monitoring

oc create secret generic grafana-datasource  --from-file=datasources.yaml  -n new-project-monitoring

* grafana-datasources -> /etc/grafana/provisioning/datasources
* grafana-dashboards ->  /etc/grafana/provisioning/dashboards
* Particular dashboards:
    * grafana-dashboard-nginx -> /grafana-dashboard-definitions/0/nginx
    * grafana-dashboard-cluster -> /grafana-dashboard-definitions/0/cluster-information
* grafana.ini -> /etc/grafana


`oc new-app -f template.yaml`


