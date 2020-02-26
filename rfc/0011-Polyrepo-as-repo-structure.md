---
date: "2020-01-16"
author: Martin Jenssen <@mjenssen>
---

# Polyrepo as repository structure

### Goals

- Get stuff done with the least amount of effort
- Must work with Git
- Must work with GitHub

### Non-goals

- Pricing

## Summary

Use separate repositories for now. If the benefits of a monorepo are strong
enough, we can create the necessary tooling to avoid the downsides of using a
monorepo in the future.

## Details

### A single monolithic repository (monorepo)

- Make it easier to contain changes in multiple areas of the codebase in a
  single commit or pull request.
- Make it easier to see all dependencies between applications, libraries, and so
  on. This is because breaking changes will be very visible if you try to build
  everything in the monorepo.
- A single commit describes the entire world.

### Several smaller repositories (polyrepo)

- Make it easier to have multiple versions of libraries as dependencies.
- Make it easier to avoid tight coupling.
- Some build/package systems require git repositories to not be part of another
  repository (or doesn’t support packages in nested folders).
- If we intend to use GitHub issues at all (at least for the open source parts),
  it might be easier to see the list for a smaller repository.

### An alternative

- Use several smaller repositories, but have a separate repository with
  submodules that describes the entire world.
- Use submodules for dependencies.

### Discussion

A monorepo will make it easier to have everything in one place, and versioning
the entire world will be easy. However, it makes it harder to version individual
pieces. While sharing code is also generally easier with a monorepo, changes in
this shared code will require you to build and test everything that depends on
this shared code. Breaking changes in the shared code will force you to fix it
everywhere instead of gradually.

Building and testing will also be more complex or more time consuming with a
monorepo. You have two choices: either let everything in the monorepo be built
and tested every time you make a change (time consuming); or have tooling that
understands which parts have been changed and only build and test those parts
(complex). Apart from the time element, the former can be viewed as a positive
as you know everything is rebuilt and tested all the time. If you have a fix to
a critical issue to a small system that you want to deploy, this can be a huge
negative though.

Possibly the biggest benefit of a monorepo is that a single commit or PR can
encompass an entire feature or change. For example, let’s say you want to add a
new button that calls a new endpoint, which calls a new microservice. All of
these can be contained in the same pull request with a monorepo, and possibly
2-3 pull requests with several repositories.

Finally, there is the question of how well a monorepo can scale with Git. Google
uses their own VCS (with a lot of additional tooling), Facebook uses Mercurial
(including a custom server for hosting their monorepo), and Microsoft has
struggled a lot with their Git monorepo (although they have contributed a lot to
the open source Git project to improve on this). Whether scalability will be an
issue or not for AtB is unclear at this point.

### Recommendation

Use separate repositories for now. If the benefits of a monorepo are strong
enough, we can create the necessary tooling to avoid the downsides of using a
monorepo in the future.
