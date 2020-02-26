---
date: "2020-01-06"
author: Rino André Johnsen <@rinoandrejohnsen-atb>
---

# Cloud Agnostic Architecture

### Goals

The main goal is to be in position where a choice of one specific cloud provider
is irrelevant for the operational workloads.

### Non-goals

## Summary

“... if I'm to choose between one evil and another, then I prefer not to choose
at all.”

Cloud Agnostic Architecture takes the idea of flexibility in public cloud
computing one step further of easily running workloads and applications within
any public cloud.

## Technical architecture, dependencies and components

Knative = Kubernetes + Istio.

- Knative is focusing on open-source-first technologies that run anywhere, on
  any cloud, on any infrastructure supported by Kubernetes.
- Knative as the underlying ‘abstraction-as-platform’, allows one to move
  workloads freely across platforms.
