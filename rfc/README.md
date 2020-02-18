# RFC/DesignDocs

For any strategic, long term or non-trivial changes (such as but not limited to,
technology decisions, architectural decision, design pattern decisions) must be
done through RFC (Request for Comments) documents (or design document) proposing
a solution. This way we document decisions and give shared ownership on
important discussions.

Any community member can add a proposal for consideration by the community at
any time. RFC proposals are intended as bigger decisions and not issues. Many
everyday changes and suggestions can be normal issues on Github issues on each
respective project repository.

A proposal should be as specific as possible, proposing a solution to a specific
problem. The document should explicitly state what solution and what problem we
are discussing. A proposal should also cover alternative approaches and a
discussion on what has been considered. The general goal is to have formal ways
of doing decisions and have documentation for future reference.

## RFC proposal flow

General flow is

1. Proposal (Pull request)
2. Discussion (PR comments)
3. Vote (if no consensus is made through discussion. Vote in comments on PR)
4. Final decision (Merge PR)

where we use Github Pull Requests and markdown documents in this folder to
communicate RFCs.

To add a new proposal, make a new markdown file in this directory using
[the template](./0000_template.md). Open Pull Requests as early as you want to
get feedback while writing. Label Pull Requests as `WIP` to explicitly mark that
this PR isn't ready for voting or lazy consensus.

When creating Pull Requests, use the Pull Request template on Github.

## Voting

[See document on voting](../VOTING.md)
