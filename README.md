# grafana-dashboards
Repository with Grafana dashboards

## Dashboards

- [Kubernetes / KSM Cluster & Service Overview](dashboards/kubernetes/ksm-kubernetes-overview-v13.json)
  - Grafana 13+ dashboard using the native v2 tabs layout.
  - Expects a Prometheus-compatible datasource named `VictoriaMetrics`.
  - Uses `k8s_cluster_name` as the primary cluster selector.
  - Provides a cluster overview tab and a service detail tab with a scoped `service_name` selector.
