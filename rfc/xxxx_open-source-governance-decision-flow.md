---
date: "2020-02-04"
author: Mikael Brevik <@mikaelbr>
relevant: RFC0001
---

# Open Source Governance and Decision flow

### Goals

- Allow for maximum external contributions
- Be as open and transparent as possible
- Have established decision flow methods
- Communicate AtB as an interesting place to work
- Align all decisions across disciplines (design, development, business)
- Ensure the quality of produced outputs (apps, infrastructure)
- Ensure AtBs overall strategic goals
- Avoid “highjacking” of projects
- Ensure safety and security are maintained in projects

### Non-goals

- Retain ownership of every decision

## Summary

I propose using meritocratic governance with voting based decision flow
according to the template based on Apache’s model (Meritocratic governance
model).

### Roles of management:

- Users: Consumers of products, SDKs, APIs, components, etc. (anyone can do
  this)
- Contributors: Answering issues, providing feedback, etc. They can also submit
  patches through PRs. (anyone can do this)
- Committers: “Elected contributors” with write access to given repositories.
- Project management committee (PMC): Strategic decisions. Elects committers.

While committers would have write access, I think we should explicitly go
through Pull Request based flow with reviewers.

### Voting:

- Lazy consensus if possible
- Voting by PMCs (or committers if we want)

Voting is based on open RFCs (request for comments) in a separate repo, tagging
what project the RFC is about.

It will be up to PMCs to adhere to the strategic goals of AtB.

---

This proposal is implemented by
[RFC0001](https://github.com/AtB-AS/org/blob/master/rfc/0001_this-repository.md)

## Discussion

Open Source is more than just disclosing the source code. It is about
communication, willingness to change and inclusiveness. To be a successful Open
Source project, we must work within the practices of Open Source. This includes
platforms, but also methodology. Having all communication and decision flow
internal will not allow the project to grow as an Open Source project and will
not have the intended effect or gains.

There are established ways of handling Open Source projects. The most prominent
models are BDFL (Benevolent Dictator for Life), meritocracies or liberal
contribution models. BDFL isn’t directly applicable in this sense as we are an
organization striving for autonomy, even though we have a product owner.

Meritocratic and liberal governance are similar. With liberal governance, you
can be accepted as an official contributor by contributing a non-trivial patch,
but in a “meritocracy” the threshold is somewhat higher.

As I see it, meritocracy is a mix of liberal and BDFL. It allows for external
contributors in the same way as internal contributors, but it is not as
consensus-driven as liberal governance. In meritocratic governance, you can be a
contributor without being allowed to vote on strategic, big picture decisions.
It is a flat structure but in addition to contributors, you have a project
management committee (PMC, initially on-team developers at the AMP team) and a
chair of PMC (typically team lead in our case?). New committers (people with
write access) can be nominated by other committers but must be voted in by PMC.

I think meritocracy is kind of stricter and less open than liberal, but I also
think this is the kind of governance this project needs for the time being. We
need to be able to do the long term strategic decisions, but also allowing for
external input. This is also important when it comes to user insight and design.
External contributors aren’t as likely to possess empiric user insight nor
actively work to gain that information. This means that we need to be able to
communicate this well enough, but also having the authority to “elevate
discussions” (vetos). Philosophically this is an escape hatch, but I think it is
necessary for the stage we are in for this project. With this model, external
committers can have write access to repositories but can be overruled and
removed as committers by PMCs.

We could also do some form of BDFL, where the “internal team” takes all
decisions but documents decisions and implements solutions without any open
communication. This would be easier to do, but I also think it will have less
impact. I think a proper Open Source Governance such as meritocratic can force
us to follow good principals such as design docs/RFCs, documentation and reduce
onboarding complexity.

I propose using meritocratic governance with voting based decision flow
according to the template based on Apache’s model:
http://oss-watch.ac.uk/resources/meritocraticgovernancemodel.

I also propose we do open RFCs (request for comments) in a separate repo,
tagging what project the RFC is about.
