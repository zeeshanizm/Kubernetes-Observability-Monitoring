# Runbook

Prerequisites: Docker Compose. This runnable local stack demonstrates Prometheus scraping a sample service and Grafana UI.

```bash
cd monitoring
docker compose up --build -d
curl http://localhost:8080/metrics
# Prometheus: http://localhost:9090
# Grafana: http://localhost:3000
```

Grafana default local credentials are typically admin/admin; change them immediately and do not expose port 3000 publicly. In Prometheus, query `up{job="portfolio-demo"}`. The alert example is in `alerts.yml` and must be loaded in Prometheus configuration before use. For Kubernetes use Prometheus Operator/kube-prometheus-stack and Kubernetes ServiceMonitor resources. EFK, centralized logs, and SLO dashboards are architectural extensions not deployed by the local Compose stack.

Teardown: `docker compose down -v`.
