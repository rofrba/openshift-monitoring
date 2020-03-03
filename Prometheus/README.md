## How to install Prometheus into an Openshift OCP

### This is an example to install Prometheus for monitoring another endpoint different to an Openshift-Monitoring project.

* Create a new project into OCP

`oc new-project  new-project-monitoring`

* Import Image from Red Hat Registry

`oc import-image openshift/prometheus:v3.11.170-5 --from=registry.redhat.io/openshift3/prometheus:v3.11.170-5 --confirm -n openshift`

* Create new app based in an image previously import
`oc new-app -i openshift/prometheus:v3.11.170-5  --name prometheus-services -n new-project-monitoring `

* Expose the service

`oc expose svc/prometheus-services`

* Edit [prometheus.yml](ConfigMaps/prometheus.yml)

* Create a ConfigMap with prometheus.yml

`oc create configmap  prometheus.yml  --from-file=prometheus.yml  -n new-project-monitoring`

* Edit the DC to mount a ConfigMap into prometheus container

`oc set volume dc/prometheus-services --add --type=configmap --configmap-name=prometheus.yml --mount-path=/etc/prometheus/prometheus.yml`

### **Optional** Add a PV to persist metrics
* Create a PVC, edit [pvc.yaml](pvc.yaml)

` oc create -f pvc.yaml -n test-https `



