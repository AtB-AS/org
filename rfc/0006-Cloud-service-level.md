---
date: "2020-01-14"
author: Jørund Leknes <@jleknes>, Erling Berg-Tesdal <@erlingt>
---

# Cloud service level (IaaS, PaaS, FaaS etc)

### Goals

- Horizontal scaling and avoid having to manage scaling manually.
- Simple integration with CI/CD.
- Limit lock-in to one of the three public cloud providers.
- Limit required work with configuration and infrastructure management.
- Allow deploy of new versions without downtime.
- Provide an environment that contributes to developer velocity and
  productivity.
- Avoid limiting choice of programming languages.

### Non-goals

- Provide an environment for running standalone servers that are stateful or
  impossible to deploy in a Docker container.

## Summary

AMP will use a market-leading cloud provider to run a selection of crafted
microservices. Relevant alternatives are Amazon Web Services (AWS), Google Cloud
Platform (GCP) and Microsoft Azure.

We recommend starting with the serverless container platform Google Cloud Run.
If we need greater control at the cost of added complexity we can utilise a
managed Kubernetes service like GKE at a later stage.

## Discussion

All three public cloud players offer services at different levels from managing
virtual machines (IaaS) to Function as a Service (FaaS).

### Alternatives:

- **FaaS**: AWS Lambda, Azure Functions and Cloud Functions
- **Serverless container** platform: AWS Fargate, Azure Container Instances
  (ACI) and Cloud Run
- **Managed kubernetes**: Amazon Elastic Container Service (EKS), Azure
  Kubernetes Service (AKS) and Google Kubernetes Engine (GKE)
- **Managed container** platform: Amazon Elastic Container Service (ECS), Azure
  Container Instances
- **Virtual machines**: Amazon EC2, Azure Virtual Machines and Google Compute
  Engine

Using an IaaS offering of virtual machines is not required to run micro
services, but it is required for specific tasks where one needs low level access
to specific kernel or GPU features.

Our needs are met by FaaS, a container service or a managed Kubernetes cluster.
The main issue with FaaS is lock-in. The service also limits which programming
languages can be used and there is an issue with latency related to cold starts.
FaaS services are an abstraction on top of other cloud offerings, and this
abstraction comes at a price premium. For rarely utilized or short lifespan work
loads they are much cheaper than other alternatives.

A managed Kubernetes cluster (GKE, EKS or AKS) introduces some complexity and
gives greater control, but takes away the need to manage the control plane of
the Kubernetes cluster.

A serverless container platform like Cloud Run provides an environment to run
containers, without the complexity of a managed Kubernetes cluster.

The pricing structure for GKE and Cloud Run differ. For GKE you will be billed
for each node in your cluster, even if you have no services deployed to them.
Cloud Run takes away a level of detail, and could be more cost effective. This
is especially true for test environments that are not heavily utilized and often
transient in nature.

If we use a serverless container engine like Google Cloud Run / AWS Fargate /
ACI we can add a managed Kubernetes solution (GKE, EKS or AKS) at a later point
if that should prove necessary.

## Figures and diagrams

The table shows the service offering of Google Cloud (taken from
https://www.youtube.com/watch?v=wzPmgWJ5fpU) and what needs make you have to
move down in the stack.

| Cloud Functions (FaaS)                |                                                                                         |
| ------------------------------------- | --------------------------------------------------------------------------------------- |
| App Engine                            | App: URL routing code sharing, traffic splitting                                        |
| Cloud Run                             | Support any programming language, run in containers                                     |
| Kubernetes Engine (hosted Kubernetes) | Hybrid, need specific OS, network protocols beyond HTTPS                                |
| Compute Engine (VM)                   | GPUs, need specific kernel, Windows, licencing requirements, migrating existing systems |
