## Prometheus

### This is an example to install Prometheus to monitor another different endpoint from the Openshift-Monitoring project.

* Create a new project into OCP

`oc new-project  new-project-monitoring`

* Edit [prometheus.yml](ConfigMaps/prometheus.yml)

* Create a ConfigMap with prometheus.yml

`oc create configmap  prometheus.yml  --from-file=prometheus.yml  -n new-project-monitoring`

* Add a PV to persist metrics

* Create a PVC, edit [pvc.yaml](pvc.yaml)

` oc create -f pvc.yaml -n new-project-monitoring `

* Create a new-app based on [template](template.yaml)

`oc new-app -f template.yaml`



