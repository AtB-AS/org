---
date: "2020-01-14"
author: Jørund Leknes <@jleknes>
---

# GCP as Cloud Provider

### Goals

- developer friendliness
- sufficient services offered
- profit from current experience in the team

### Non-goals

- Lowest cost alternative. We do not yet know enough about which services we
  will use to calculate the cost.

## Summary

We need to select one of the three major players (AWS, Azure, GCP) as the public
cloud platform for AMP.

We will use Google Cloud Platform for AMP for the first iteration to reduce
latency with the use of Entur AS's infrastructure.

## Discussion

### Alternatives

- AWS
- Azure
- GCP

Entur is using Google Cloud. Using GCP for AMP might reduce latency and cost.
Using a different platform might make us a bit more vulnerable to incidents. If
we for example use AWS, outages at both AWS and GCP will affect us.

GCP is also preferred by more developers on the team than AWS or Azure.
