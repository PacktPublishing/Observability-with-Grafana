## Setup Instructions

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
