---
date: "2020-04-15"
author: Mikael Brevik <@mikaelbr>
---

# Backend for Frontend as logic component

### Goals

- Reduce data payload out to clients
- Simplify/Reduce the amount of client-specific domain logic on client sides
- Increase data aggregation robustness
- Better allow for continuous updates of data-layers for clients.
- Reduce CPU load and battery usage of clients

### Non-goals

- Routing everything through a singular backend (not a goal to be a transparent
  proxy "shims")
- Co-locate general business and domain logic or be a public API.
- Specify language/runtime of BFF

## Summary

I propose an architectural artifact for handling client-side communication on
specific data transformation (as close to UI data form as sensible). Commonly
known as a backend for frontend (BFF).

A BFF is meant as a single-purpose edge service for UIs and other consumers. But
the key part is it limits work on the clients, allow to group features that are
the same, make it easier to roll out new changes and patch fixes to data
management for apps. A BFF is a part of the client itself it just happens to be
hosted as a separate service in a microservice architecture.

Currently, this RFC says nothing on the specific technology (language or
runtime) of BFFs, this can be it's own RFC. But I think it stands to reason as
it is an extension and part of the client-side implementation it self it's
natural to look at the same technologies and runtimes to achieve some sort of
interoperability (e.g. types).

## Discussion

When doing client-side development using microservice architecture in an
ecosystem that should be highly available and accessible, there are some
challenges. A non-exhaustive list includes unnecessary large payload sizes,
unnecessary traffic due to rate limiting, retries and API orchestration,
unnecessary CPU cycles for algorithms and data transformation, and handling data
and API deprecations. The latter point is especially important in a mobile app
setting, where we have less control over what version users have and we can't
easily force update versions. This means it is harder to do continuous
development if the codebase is stored exclusively on client devices. This also
goes for "downstream" changes (to service layer), where a BFF can add
flexibility to adapt changes from lower layers.

We also have a case where we have several data sources that are general purpose
and can be used in many different ways but require a specific orchestration and
transformation to be usable for our clients. These include things like geocoding
reverse lookup for search completion (typeahead), searching for journey/trips
between two locations, showing departures nearby, etc. These are concrete
user-driven requirements which include data transformation choices which are not
general-purpose, but specific for a given app or web screens.

The BFF should not be a tool to achieve DRY codebases or to have a catch-all
solution for APIs between other services, and it introduces additional costs and
overhead for infrastructure, but in a runtime where we have code first
infrastructure I think the overhead is minimal and the gains are way larger than
the costs.

Features as mentioned before (reverse lookup, finding journeys or showing nearby
departures) are features we can handle very specific and be ad-hoc for UI layers
and optimized for what we want to prioritize. E.g. sorting objects, picking
correct fields (projection, to reduce payload), merging data (like quays/stops
in reverse address lookup), etc. They are specific usages of general data that
are only relevant for our presentational needs. But it is still the same
specific usages for our app _and_ web clients. For the travel planner, the
current hypothesis is that we will have a similar search behavior on the web.
It's unnecessary to handle these things on the client and risk fragmentation of
data and inconsistent information. We should be sure that apps and web clients
show the same result.

I don't think it's a catch-all solution, and I think it can be overused. At some
point it can be that we are better served to generalize code as a separate
service (move to the service layer, not specific for UI), and not use the same
BFF for both web and client. But thinking of overlapping user needs and user
interactions I think view specific transformation is the same for both web and
app.

Might be at some point web and app shouldn't share the same BFF, but even with
specific BFFs for apps, it has added benefit due to easier deployment and
distribution of new versions. Being able to tweak, optimize and fix issues with
data layer continuously without waiting for users to update their apps is a huge
advantage. This can be achieved by moving view specific logic to a BFF and keep
clean view state management in the app itself.

### Resources

Other descriptions and thoughts on BFFs:

- https://samnewman.io/patterns/architectural/bff/
- https://nordicapis.com/building-a-backend-for-frontend-shim-for-your-microservices/
- https://docs.microsoft.com/en-us/azure/architecture/patterns/backends-for-frontends
