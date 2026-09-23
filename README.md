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

- [OpenTelemetry Python Overview v3](dashboards/python/otel-python-overview-v3.json)
  - Grafana 13+ dashboard using the native v2 resource model.
  - Expects a Prometheus-compatible datasource named `VictoriaMetrics`.
  - Covers Python process CPU, physical and virtual memory, threads, file descriptors, disk I/O, and CPython garbage collection.
  - Requires `opentelemetry-instrumentation-system-metrics` and its `psutil` dependency to be installed and loaded by Python auto-instrumentation, with a metrics exporter configured. The regular OpenTelemetry Python SDK does not emit runtime process metrics by itself.
  - Uses the current `process.*` metrics and avoids the deprecated `process.runtime.*` metrics.
  - Expects Prometheus-compatible metric and label names, such as `process_memory_usage_bytes` and `cpython_gc_collections_total`. When ingesting OTLP directly into VictoriaMetrics, enable `-opentelemetry.usePrometheusNaming`.
  - Provides optional `service_namespace`, `service_name`, and `service_instance_id` selectors. Open file descriptor data is unavailable on Windows, and process disk I/O requires a recent system-metrics instrumentation release.
