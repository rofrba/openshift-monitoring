## How to install Prometheus into an Openshift OCP

`oc new-project  new-project-monitoring`

`oc import-image openshift/prometheus:v3.11.170-5 --from=registry.redhat.io/openshift3/prometheus:v3.11.170-5 --confirm -n openshift`

`oc new-app -i openshift/prometheus:v3.11.170-5  --name prometheus-services -n new-project-monitoring `

`oc expose svc/prometheus-services`

Editar prometheus.yml

`oc create configmap  prometheus.yml  --from-file=prometheus.yml  -n hello-dev`

`oc set volume dc/prometheus-services --add --type=configmap --configmap-name=prometheus.yml --mount-path=/etc/prometheus/prometheus.yml`


[Config Maps mounts](ConfigMaps)
* prometheus.yml ->  /etc/prometheus

## Persistent Volume mount
* prometheus-db -> /prometheus

