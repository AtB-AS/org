---
date: "2020-01-15"
author: Jørund Leknes <@jleknes>, Martin Jenssen <@mjenssen>
---

# Observability in the cloud for backend services

### Goals

- Observe performance through the entire stack to detect bottlenecks or
  inperformant queries.
- Get precise statistics on number of queries, usage, peaks etc.
- Support alerts and triggers based on metrics and logs.
- Be able to monitor feature usage.
- Offer a centralized service for logging from all applications.
- Interface to help debug when a report occurs.
- Server side components / cloud services should preferably be possible to
  configure with terraform.
- Ease of configuration
- Access our cloud infrastructure health and metrics and application logs and
  metrics through the same interface
- Easy to implement on the application side
- Low overhead and performant application side implementation

### Non-goals

- Avoiding sensitive privacy data in logs is the responsibility of the
  application.
- Alerts and triggers is handled by another service.
- Front-end analytics to track user behaviour.

## Summary

We will standardize on a common framework for logging, metrics and tracing for
AMP backend services (including backends for frontend). This design document is
based on GCP.

We will use Google Stackdriver as our logging, metrics and tracing backend.
Applications will log to standard out for logging and use Openmetrics and
Opentracing for metrics and tracing.

## Discussion

### Alternatives for logging service:

- Google Stackdriver
- ELK
- Splunk
- Graylog

### Alternatives for metrics:

- OpenCensus (application side)
- Stackdriver monitoring API (application side)
- Google Stackdriver
- Prometheus (either managed service or self hosted at GCP)

### Alternatives for tracing:

- Opentracing / Opentelemetry (application side)
- Google Cloud Stackdriver (server side)
- Jaeger tracing (server side)

On the service level we can either use Google Cloud Stackdriver or a combination
of ELK / Graylog / Prometheus and Jaeger.

On the application side there exists open standards like Opentracing and
Opencensus that can be utilized both with Stackdriver and Jaeger/Prometheus.
There are also some proprietary APIs like Stackdriver monitoring API.

### Arguments

Using open standards on the application side reduces lock in compared to using
proprietary APIs like Stackdriver monitoring API. Stackdriver provides lowest
complexity with regards to setup and management. Use of self hosted solutions
like ELK and Prometheus requires handling of software updates manually.
Stackdriver provides one solution for tracing, metrics and logging. This reduces
complexity.

### Conclusion

We will use Google Stackdriver as our logging, metrics and tracing backend. On
the application side we will use standard out, Openmetrics and Opentracing for
logging, metrics, and tracing.
