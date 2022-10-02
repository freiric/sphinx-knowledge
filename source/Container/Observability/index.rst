Observability
===================

- standard: CNCF `Cloud native Computing Foundation <https://landscape.cncf.io/?project=graduated,incubating>`_
- Correlation for log, integration with SAP
- Integration in our build stack (Spring, K8S)



new relic? 

- Traces : A trace follows a program flow with detailed  technical information, mainly used to find performance bottleneck, and in case of error to find how you get there.
  Trace will typically be analyzed by program.
- Logs : A log is a discrete event that the programmer deemed interesting enough to be logged. The most important use case for logs is error reporting, but there may be other categroy  ordered by their level of importance or details: warning, debug, info and trace.
- Monitoring : is collecting, aggregating and analyzing metrics, these can be memory disk space available, throughput. The metric can come from the cluster, the node, (the pod for k8s), the container, the application.

Logs
****************

buzzwords:
Datadog?


Complete logging soluttions
+++++++++++++++++++++++++++++++

- ELK  = Elastic Search - Logstash/fluentd - Kibana
- Loki (promtail as shipper)  - Grafana
- Splunk? ->  commercial
- Graylog -> open source



Log shiper
+++++++++++++++

- fluentd : logs shipper, tansform to json as soon as possible - **CNCF graduated**
- Logstash : logs shipper - pros flexible due to lot  of plugins, cons: perf
   


Tracing
**********

complete solution
+++++++++++++++++++++

- Sleuth - Brave - `Zipkin <https://zipkin.io/>`_
- Open Telemetry - Jaeger

- `Grafana tempo <https://grafana.com/oss/tempo/>`_

Brave: `Brave <https://github.com/openzipkin/brave>`_ tracing instrumentation.
Jaeger: **CNCF graduated**

API : https://opentelemetry.io/docs/instrumentation/java/

Metrics
************

Prometheus - Grafana

prometheus: **CNCF graduated**


Example:
************

- `boot-opentelemetry-tempo <https://github.com/mnadeem/boot-opentelemetry-tempo>`_: 

    This project demonstrates Observability using:

	- Prometheus for monitoring and alerting
	- Loki for Distributed Logging
	- Tempo for Distributed Tracing
	- Grafana for visualization

    And basically integrates the following

	- Opentelemetry
	- Grafana Tempo Which internally uses Jaeger
	- Spring Boot Project
