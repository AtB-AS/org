---
date: "2020-02-04"
author: Rino Andre Johnsen <@rinojohnsen-atb>, Mikael Brevik <@mikaelbr>
---

# Open Source Strategy

### Goals

- Share as much of our work and knowledge as Open Source.
- Involve community and Trondheim in the development and design of a new
  solution
- Be visible as a development organization to show AtB as an attractive
  workplace.
- Get valuable external input from others outside AtB

### Non-goals

- Risk safety/security breaches
- Break NDA with Entur AS

## Summary

We should default to Open Source development and methodology, and consider case
by case if information or solutions should be made private.

There are some things that are crucial for this to work. All variables and
configuration items should be stored in external storage outside of
repositories. We cannot share any code from Entur which is not explicitly
licensed as Open Source, or any features or APIs marked as private.

While ensuring security, privacy and safety is up catered for, we should strive
to be as open as possible (\* see Design Doc on Open Source Governance and
Decision flow:
https://docs.google.com/document/u/1/d/1-tW8d9UdIwPt4pq7bJn0dlDRuoGIV7HaeENpDsS_MZY/)

- Secrets should be Environment Variables or Secret Storage (preferably env.var)
- Private repositories from Entur should never be made public.

## Discussion

AtB is publicly financed by the county through taxation. As such it can be
considered public domain in a sense. More than that, Trondheim has a long
tradition of doing derived work with AtB data and solutions both through Open
Source and reverse engineering work. This is something we should embrace instead
of counteracting. We should use the enthusiasm of the community to make better
products and better services for the people of Trondheim. This is why we should
strive to be as open as possible. This can also give the added effect of making
AtB a more attractive workplace for many, which is important should it (want to)
build an internal culture of software development.

Ensure the safety of internal tokens and Entur tokens. Environment Variables
should be used only in build time and run time and should be nowhere near any
public repo.

### What cannot be Open Sourced

- Private repositories forked from Entur AS can under no circumstances be made
  public without explicit sayso from Entur AS.
- Integration libraries developed by Entur AS should not be Open Sourced.
- Snippets found within private code from Entur can under no circumstances be
  made public without explicit sayso from Entur AS.
- Code we use where someone else has the license and the license is not of open
  source type.
- API secrets, keys, and other tokens. (This also includes in readmes)
- Entur AS partner token or any other tokens from Entur AS
- Real user data and user information.
- Information that can hurt the goal of AtB or AtB as an organization should
  never be open-sourced.

### Best practices and routines

- If tokens, keys or secrets are published, we must immediately recycle the
  tokens. If not possible we either have to rewrite history or consider deleting
  repository.
- If user details are leaked (it at no point should be) we have to immediately
  rewrite history or terminate the repository.
- All secrets, keys, and tokens should be as environment variables, for both:
  - Supporting multiple environments and scaling
  - Hiding details
- Secrets should not be part of Dockerfiles.
- When using a significant part of code (from other projects) we have to check
  the license and possibly refer to the source.
