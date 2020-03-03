## Grafana

`oc import-image openshift/grafana:6.5.2 --from=grafana/grafana:6.5.2 --confirm -n openshift`

`oc new-app -i openshift/grafana:6.5.2  --name grafana -n openshift-metrics `

`oc expose svc/grafana`


[Config Maps mounts](ConfigMaps)

* grafana-datasources -> /etc/grafana/provisioning/datasources
* grafana-dashboards ->  /etc/grafana/provisioning/dashboards
* Particular dashboards:
    * grafana-dashboard-nginx -> /grafana-dashboard-definitions/0/nginx
    * grafana-dashboard-cluster -> /grafana-dashboard-definitions/0/cluster-information
* grafana.ini -> /etc/grafana


