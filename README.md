# RedHatInsights/tower-analytics-saas-templates

# Grafana dashboards

Grafana is a web application for monitoring status of services using graphs and charts. 

Development RH documentation can be found there:
- [Add a Grafana Dashboard](https://gitlab.cee.redhat.com/service/app-interface#add-a-grafana-dashboard)
- [Monitoring](https://gitlab.cee.redhat.com/service/app-interface/-/blob/master/docs/app-sre/monitoring.md#VisualizationwithGrafana)

## Dashboard location

Links to Grafana instances can be found in the links for stage/prod cluster (see [doc](https://gitlab.cee.redhat.com/service/app-interface/-/tree/master/docs/cloud.redhat.com/dev-onboarding#accessing-stage-environment)).  
In the Grafana, these dashboards are available under:

- Insights > Automation Analytics
- Insights > Automation Analytics - Usage Metrics

## Dashboard definitions

Dashboards can be found in [dashboards folder](dashboards).  

These ConfigMaps are generated from exported JSON. 

Dashboard can exported in Grafana by:
- Save button (top right corner of dashboard) > Copy JSON to Clipboard

### Convert JSON to ConfigMap

App-Interface needs configmap for deployment of dashboard.  
The conversion script is located in [./convert-json-to-configmap.sh](./convert-json-to-configmap.sh) script

Save the json to the dashboard folder:
- increase the "version" (bottom of the file)  - check current yaml
- and run:

```
oc login <some openshift>

cd dashboards

../convert-json-to-configmap.sh -f <your-file.json>
```


## Publishing dashboard

The last operation is to release the dashboard to the App Interface. 

Update the [saas-grafana.yaml](https://gitlab.cee.redhat.com/service/app-interface#add-a-grafana-dashboard) and either add 
a new dashboard location or update the ref to the GitHub commit of your PR with change

