---
date: "2020-09-24"
author: Mikael Brevik <@mikaelbr>
---

# GPLv3, Apache-2.0 Licence type

### Goals

- Ensure AtB is not held liable if something doesn’t work.
- Have AtB and AtBs software and documentation Open Source
- Be able to use other work with the most common licenses
- Be able to use Entur AS’s Open Source code
- Be able to use Entur AS’s secret libraries

### Non-goals

- Prevent people from making custom travel planning apps

## Summary

For big releases such as apps, web apps, and BFFs, we should use GPLv3. But for
the compatibility clause to be used we must have our own library or code base
with GPLv3 which is merged with EUPL-1.2.

| Type of project                                           | License      |
| --------------------------------------------------------- | ------------ |
| SDK, Libraries not dependent on Entur                     | Case by case |
| Component Libraries, Design Systems, Style Guides         | Case by case |
| SDK based on Entur                                        | GPLv3        |
| Documentation                                             | CC-BY-SA 3.0 |
| Proxy servers, middleware, BFF                            | GPLv3        |
| Apps, CLIs, Web-apps                                      | GPLv3        |
| Other supporting projects (like blog tools, plugins, etc) | Apache-2.0   |

## Discussion

When deciding license type for a project, there are two aspects to consider:
technical limitations and overall project goals.

Technical limitations, in this case, means our sizable direct dependencies (e.g.
bundled with our bundle). If our dependencies are non-permissive copyleft
licenses (or viral licenses), we also have to have a similar compatible license.

There is also the question of the overall project goal. Should our goal be to
enforce consumers to Open Source (viral license) or have a license that is
“easier” to work with (permissive licenses)?

### Technical limitation (dependencies)

The one dependency we cannot avoid is Entur. Our systems will be based on their
infrastructure and code. It’s worth considering what license they use and how it
affects us. Entur uses EUPL-1.2 for all of their Open Source projects. EUPL-1.2
is a copyleft license (stays “forever” the same license, and derived work must
inherit license\*) which requires attribution and disclosing source code. It
provides legal protection, preventing liability. EUPL-1.2 has an additional
compatibility clause, where you can use EUPL-1.2 for your derived work if
compatibility is required, and use other licenses. Compatible licenses include
LGPL, GPL (v2 and v3), MPL, AGPL, and others. “If required” is a key component.
From reading EUPL-1.2 license it looks like you can only use the compatibility
clause if (IFF) compatibility is required.

There are some internal libraries are unlicensed. If we are to directly use the
secret helper libraries, we have to have a license or introduce a layer for
communicating with the solution that is not SDK/code based. For instance gRPC,
HTTP, etc. We have to consider in what way we use the libraries and see how they
are licensed. It is reasonable to think that these libraries will be using
EUPL-1.2 if formalized.

It is important to remember though, virality in licensing is mostly concerned
about distribution. If we don’t distribute code with EUPL licensing, we don’t
have to inherit (with or without compatible licenses) the license type. With
licensing, there is also a concept of “reasonable distance”. This means for
instance if we use Enturs APIs with some licensing, we don’t have to use the
same license. This can also be true for libraries. If we have closed source
servers with some pipeline based API (REST, gRPC, Sockets, etc), we don’t have
to use the same license. As far as I can see, using products generated from
copyleft licenses (e.g. QR codes) won’t count as derived work and won’t impact
license choice.

Entur also has an SDK that is intended to be used bundled with distributions.
The copyleft clause comes into effect here. In our case, this is relevant for
our BFF, and clients (both native and web). This means if we want to use the SDK
directly, our license on distributed code must be EUPL license also.

The EUPL-1.2 License is “upstream” (meaning can use/link) compatible with more
permissive licenses such as MIT, BSD, etc. This means there is nothing about
EUPL which limits us from using common libraries in the React Native or web
ecosystem
(https://joinup.ec.europa.eu/collection/eupl/matrix-eupl-compatible-open-source-licences).
It is also compatible with say GPLv2 and GPLv3 licenses as EUPL-1.2 Licensed
work can be distributed with “similar” licenses if required. EUPL is similar to
GPLv3 but considered simpler
(https://joinup.ec.europa.eu/collection/eupl/news/eupl-or-gplv3-comparison-t).

![Merging with GPLv2](./image1.png)

![Merging with permissive](./image2.png)

Using EUPL doesn’t require consumers to inherit license unless they distribute
in any form. This means if they make applications or packages (e.g. NPM
packages) they need to use the same license (see
[Guidelines for Users and Developers](https://joinup.ec.europa.eu/sites/default/files/inline-files/EUPL%201_1%20Guidelines%20EN%20Joinup.pdf)).

### Using copyleft with App Store

There are some cases where GPLv2 has been in conflict with the Apple App Store
model as they add some DRM features and redistributes packages
(https://www.engadget.com/2011/01/09/the-gpl-the-app-store-and-you/). But it
looks like this isn’t applicable for GPLv3 or EUPL.

### Conclusion

If we base our code on the SDK, we are required to distribute our code as a
license similar to EUPL also. We could have the BFF as GPLv3 but our own SDK
(which cannot be based on Enturs SDK or be too similar) which has a more
permissive license if we want and that is needed. This might mean we cannot
reuse types across different clients/solutions. Other than this, most
infrastructure code uses Enturs data from REST APIs or GraphQL and not
distributing the code directly. If we use the SDK or derive our work from it, we
must be EUPL (or compatible), if not we are free to choose. AppStore
distribution model doesn’t seem to affect us unless we choose GPLv2.

## Overall project goal

Now that we know the technical limitations we can discuss the more philosophical
and strategic goals and how we want to work with Open Source. It comes down to
the question: Do we want our License to be viral, or not and how does this
affect collaboration with other counties and mobility providers.

I think the ultimate goal of this project is to reduce non-public transport in
Trøndelag county and be as transparent and open as possible to consumers. We
should be a partner of the people, other counties and Entur AS.

At least in frontend (mobile and web development), LGPL and more permissive
licenses (MIT, BSD, etc) are more common. It can be valuable conforming to more
industry-standard licenses.

### Some limitations of copyleftism and commercial platforming

If we at some point want to make SDKs for clients wanting to integrate to a
mobility platform, copyleft might be a hinderance. For instance having an
electric scooter provider wanting to integrate with our platform, they could be
required to open source their platform integration module, exposing internal
systems. Which can be a no-go and detrimental to our strategic plans. For this
we need to do case-by-case decisions if we need a more permissive license than
GPLv3.

## Conclusion

The EUPL-1.2 looks like an interesting license that is designed to be compatible
with other licenses but also copyleft. I think using EUPL-1.2 is a viable
option, but copyleft isn't always the right choice for every distributable. The
compatibility clause of the EUPL-1.2 means **we can use a more common license
type such as GPLv3**. But for the compatibility clause to be used we must have
our own library or code base with GPLv3 which is merged with EUPL-1.2.

I think using an even more common license by default for our libraries should be
preferred. End products should be more viral as we want to encourage sharing
experiences. Using a library is one thing, but redistributing entire
applications is another. The latter example I think it is more important to be
copyleft. So I think **using EUPL-1.2s compatibility with GPLv3** is
interesting. As we can maximize usage (working towards the goal of minimizing
non-public transport), but also if someone forks/redistributes our projects,
they must inherit the GPL license.

GPLv3 can be a good fit for the infrastructure code. As this will be as an end
product in many ways. People can use it as APIs without inheriting license, but
if they redistribute the license should be inherited.

An overall guide for license looks like this:

| Type of project                                           | License      |
| --------------------------------------------------------- | ------------ |
| SDK, Libraries not dependent on Entur                     | Case by case |
| Component Libraries, Design Systems, Style Guides         | Case by case |
| SDK based on Entur                                        | GPLv3        |
| Documentation                                             | CC-BY-SA 3.0 |
| Proxy servers, middleware, BFF                            | GPLv3        |
| Apps, CLIs, Web-apps                                      | GPLv3        |
| Other supporting projects (like blog tools, plugins, etc) | Apache-2.0   |
