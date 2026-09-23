# grafana-dashboards
Repository with Grafana dashboards

## Dashboards

- [Kubernetes / KSM Cluster & Service Overview](dashboards/kubernetes/ksm-kubernetes-overview-v13.json)
  - Grafana 13+ dashboard using the native v2 tabs layout.
  - Expects a Prometheus-compatible datasource named `VictoriaMetrics`.
  - Uses `k8s_cluster_name` as the primary cluster selector.
  - Provides a cluster overview tab and a service detail tab with a scoped `service_name` selector.

- [OpenTelemetry JVM Overview v3](dashboards/jvm/otel-jvm-overview-v3.json)
  - Grafana 13+ dashboard using the native v2 resource model.
  - Expects a Prometheus-compatible datasource named `VictoriaMetrics`.
  - Covers JVM CPU, heap and memory pools, garbage collection, platform threads, and class loading.
  - Uses stable JVM runtime metrics emitted by OpenTelemetry Java auto-instrumentation.
  - Expects Prometheus-compatible metric and label names, such as `jvm_memory_used_bytes` and `service_name`. When ingesting OTLP directly into VictoriaMetrics, enable `-opentelemetry.usePrometheusNaming`.
  - Provides optional `service_namespace`, `service_name`, and `service_instance_id` selectors. Ensure these resource attributes are promoted to metric labels by the metrics backend or Collector pipeline.
