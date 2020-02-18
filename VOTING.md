# Voting

Voting is only done if no _lazy consensus_ is made. Lazy consensus essentially
means if no one objects within a reasonable time it passes.

## Lazy consensus timeout

It is important to give everyone the appropriate time and information to be able
to object. Appropriate time depends on different factors such as season. In the
summertime when people are generally on vacation, you cannot propose a rewrite
of the entire infrastructure and hope no-one notices. Similarly, we should
ensure all committers with a stake in the decision (e.g. app developers,
infrastructure maintainers, etc) is aware of proposals by adding them as
reviewers of said proposal.

Big picture decisions and strategic decisions will not use lazy consensus but go
straight to voting. Also, if no lazy consensus is made we do formal voting.

## Formal voting

In formal voting, all community members are encouraged to express their
opinions, but only commmitters and/or members have binding votes for the final
decision.

The voting process is based on
[Apaches model](http://oss-watch.ac.uk/resources/meritocraticgovernancevoting)
but summarized and adapted in this document.

Voting is done directly in Pull Requests or Issues by adding your vote as a
comment.

The different votes are:

- `+1` ‘yes’, ‘agree’: also willing to help bring about the proposed action
- `+0` ‘yes’, ‘agree’: not willing or able to help bring about the proposed
  action
- `-0` ‘no’, ‘disagree’: but will not oppose the action’s going forward
- `-1` ‘no’, ‘disagree’: opposes the action’s going forward and must propose an
  alternative action to address the issue (or a justification for not addressing
  the issue)

Proposals requiring formal voting should be labeled with `Voting required` and
explicitly state the decision level (noted below).

### Decision levels

There are two different vote levels:

1. General – All `Committers` and `Members` can vote
2. Elevated – Only `Members` can vote

Decisions can be elevated from general by request on proposal.

### Required voting

There are different types of required voting, as explained in this table

| Action              | Description                                                                                                                             | Approval type                  |
| ------------------- | --------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------ |
| Technical decisions | Most technical discussions and everyday decisions.                                                                                      | Lazy consensus, General voting |
| Strategic decisions | Big picture, or strategic decisions. Important for AtB as an organization and impact outside just these projects (e.g. political, etc). | Elevetad voting                |
| New committers      | New committer has been nominated. (Not RFC, but Github Issue)                                                                           | Elevated vote                  |
| Committer removal   | Proposed removal of committer (due to inactivity or other reasons. Not RFC, but Github Issue)                                           | Elevated vote                  |
