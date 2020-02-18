# AtB Community `v0.1`

This document describes how to best work with Open Source and AtB. The main goal
of this document is transparency to the model, and to encourage new and existing
contributors.

The governance model is based on (but adapted for this purpose) the
[Apache governance model](http://oss-watch.ac.uk/resources/meritocraticgovernancemodel).

## Vocabulary

- **`User`**: Any user or general consumer of the infrastructure, API or code.
- **`Contributor`**: Any developer or designer contributing to the AtB projects.
  Either by supporting new users, improving documentation, patching code,
  identifying requirements, or more. There are many ways to contribute that add
  high value.
- **`Committer`**: Any developer or designer with write access to any
  repositories. You can be a committer of one project or more. `Committers` are
  chosen by contributing a fair amount to the project and voted in by `members`.
  Any committer or `member` can nominate `committers`. `Committers` have voting
  right for [RFCs](./rfc).
- **`Member`**: Any member of the AtB team. A `member` has `@mittatb.no` emails.
  Same as committers, but can also vote on strategic long term decisions.

## Committer onboarding

All contributors with a significant amount of work can be elected as a
`committer` by the `member` committee. Committers are elected through a voting
process and any committer or member can nominate a contributor as a potential
committer.

Committers will have write access to the project they are committers of, but
will still have to follow normal procedures with Pull Requests and reviews as
the rest of contributors, committers and members. See
[general contribution guide](./CONTRIBUTING.md).

## Voting, consensus, and decisions

For any strategic, long term or non-trivial changes (such as but not limited to,
technology decisions, architectural decision, design pattern decisions) must be
done through RFC (Request for Comments) documents proposing a solution. This way
we document decisions and give shared ownership on important discussions. But
any community member can add a proposal for consideration by the community at
any time.

General flow is

1. Proposal (Pull request)
2. Discussion (PR comments)
3. Vote (if no consensus is made through discussion)
4. Decision (Merge PR)

Voting is only done if no _lazy consensus_ is made. Lazy consensus essentially
means if no one objects within a reasonable time it passes. It is important to
give everyone the appropriate time and information to be able to object.

Read more on [RFCs and voting](./rfc) in the RFC-directory.
