# Observability-with-Grafana

This is the code repository for Observability with Grafana, published by Packt




## Setup Instructions

### Chapter 3

#### OTEL-Creds.yaml

in sections `config.extensions` and `config.exporters`

1. Replace <TRACE_USERNAME>, <TRACE_PASSWORD> and <TRACE_ENDPOINT> with details from Tempo
2. Replace <METRIC_USERNAME>, <METRIC_PASSWORD> and <METRIC_ENDPOINT> with details from Prometheus
3. Replace <LOG_USERNAME>, <LOG_PASSWORD> and <LOG_ENDPOINT> with details from Loki

Username should be a number
Password is a long token that is set up via the `Access Policies` screen in the Grafana Cloud Portal
Endpoint will look similar to these

* `tempo-us-central1.grafana.net:443`
  * This is expected to look different to the other endpoints
* `https://prometheus-prod-10-prod-us-central-0.grafana.net/api/prom/push`
* `https://logs-prod3.grafana.net/loki/api/v1/push`

#### Install OpenTelemetry collector

1. Add the OpenTelemetry Helm repository:
```console
helm repo add open-telemetry https://open-telemetry.github.io/opentelemetry-helm-charts
```

2. Install the OpenTelemetry Collector
```console
helm install --version '0.73.1' --values chapter3/OTEL-Collector.yaml --values OTEL-Creds.yaml owg open-telemetry/opentelemetry-collector
```

3. Validate the installation is running
```console
kubectl get pods

NAME                                           READY   STATUS    RESTARTS   AGE
owg-opentelemetry-collector-6b8fdddc9d-4tsj5   1/1     Running   0          2s
```

#### Install OpenTelemetry Demo application

1. Install the OpenTelemetry Demo Application
```console
helm install --version '0.26.0' --values Otel-demo.yaml owg-demo open-telemetry/opentelemetry-demo
```

2. Validate the applications are running
```console
kubectl get pods --selector=app.kubernetes.io/instance=owg-demo

NAME                                              READY   STATUS    RESTARTS   AGE
owg-demo-emailservice-68d874d8dc-xf2lv            1/1     Running   0          5m
owg-demo-frontendproxy-7f647bccf9-fdf8t           1/1     Running   0          5m
owg-demo-quoteservice-6cd6cb9476-jvlff            1/1     Running   0          5m
owg-demo-productcatalogservice-dd9d84d67-5sbx8    1/1     Running   0          5m
owg-demo-paymentservice-79fcbf6888-fs7fd          1/1     Running   0          5m
owg-demo-redis-578cdb6447-84x7d                   1/1     Running   0          5m
owg-demo-loadgenerator-b9ffd5d4f-m7g69            1/1     Running   0          5m
owg-demo-ffspostgres-6695d47498-kr6m5             1/1     Running   0          5m
owg-demo-kafka-58cdf5dbbc-fkh2h                   1/1     Running   0          5m
owg-demo-shippingservice-66dd4f4b8c-2lndp         1/1     Running   0          5m
owg-demo-recommendationservice-c57c5dfbd-bpx8c    1/1     Running   0          5m
owg-demo-frontend-7465547d4d-kmv7d                1/1     Running   0          5m
owg-demo-currencyservice-58b65ccd89-rrxkv         1/1     Running   0          5m
owg-demo-adservice-5678b98bcd-jz82b               1/1     Running   0          5m
owg-demo-cartservice-98468fff7-h9dz8              1/1     Running   0          5m
owg-demo-featureflagservice-7847d8f7f7-7hnrq      1/1     Running   0          5m
owg-demo-accountingservice-8596699678-8t88f       1/1     Running   0          5m
owg-demo-checkoutservice-7585d7d45f-zgrpp         1/1     Running   0          5m
owg-demo-frauddetectionservice-555bcff644-b6ktm   1/1     Running   0          5m
```

3. Open port for frontendproxy access
```console
kubectl port-forward svc/owg-demo-frontendproxy 8080:8080 &
```

4. Open port for browser spans
```console
kubectl port-forward svc/owg-opentelemetry-collector 4318:4318 &
```

5. Check access to the OpenTelemetry Demo application
In your browser head to (http://localhost:8080)

### Chapter 4

The changes to the OpenTelemetry collector for chapter 4 will add a lot of additional labels to logs, and collect Kubernetes events from the cluster.

#### Upgrade the OpenTelemetry collector

1. Upgrade the OpenTelemetry Collector
```console
helm upgrade --version '0.73.1' --values chapter4/OTEL-Collector.yaml --values OTEL-Creds.yaml owg open-telemetry/opentelemetry-collector
```

2. Validate the installation is running
```console
kubectl get pods --selector=component=standalone-collector

NAME                                           READY   STATUS    RESTARTS   AGE
owg-otel-collector-594fddd656-tfstk   1/1     Terminating   1 (70s ago)   2m8s 

owg-otel-collector-7b7fb876bd-vxgwg   1/1     Running       0             3s 
```

### Chapter 5

The changes to the OpenTelemetry collector for chapter 5 will add a lot of additional metrics, from the Kubernetes cluster, the Kubelet running on a node, the host itself and the collector too.

#### Upgrade the OpenTelemetry collector

1. Upgrade the OpenTelemetry Collector
```console
helm upgrade --version '0.73.1' --values chapter5/OTEL-Collector.yaml --values OTEL-Creds.yaml owg open-telemetry/opentelemetry-collector
```

2. Validate the installation is running
```console
kubectl get pods --selector=component=standalone-collector

NAME                                           READY   STATUS    RESTARTS   AGE
owg-otel-collector-594fddd656-tfstk   1/1     Terminating   1 (70s ago)   2m8s 

owg-otel-collector-7b7fb876bd-vxgwg   1/1     Running       0             3s 
```

### Chapter 6

The changes to the OpenTelemetry collector for chapter 6 will collect metrics generated from the trace data collected, and add additional information used by Tempo to display service maps.

#### Upgrade the OpenTelemetry collector

1. Upgrade the OpenTelemetry Collector
```console
helm upgrade --version '0.73.1' --values chapter6/OTEL-Collector.yaml --values OTEL-Creds.yaml owg open-telemetry/opentelemetry-collector
```

2. Validate the installation is running
```console
kubectl get pods --selector=component=standalone-collector

NAME                                           READY   STATUS    RESTARTS   AGE
owg-otel-collector-594fddd656-tfstk   1/1     Terminating   1 (70s ago)   2m8s 

owg-otel-collector-7b7fb876bd-vxgwg   1/1     Running       0             3s 
```
