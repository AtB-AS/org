---
date: "2020-03-31"
author: Mikael Brevik <@mikaelbr>
---

# Quality assurance flow for apps

### Goals

- Ensure rapid progress
- Ensure quality of tasks completed
- Establish shared ownership of tasks and have full transparency
- Have trackable, contextualized, feedback.
- Reduce critical issues from being released.

### Non-goals

- Prevent any bug from being released
- Act as feature gatekeeping

## Summary

This RFC establishes a routine for development flow and quality assurance with
app development. This document covers needs and suggestions of implementation
and is accompanied by an implementation through
[the QA progress guide](../guides/workflow-and-qa-progress-apps.md).

We need a structured way to work with QA to do rapid development but still
ensure that the quality of our service is up to our standards. We can also use
this process to better the communication between design and development as a
dialogue. The QA should be gatekeeping for features but stop critical bugs from
making their way to the end-user. We also have to ensure that our implementation
follows rules for universal design.

**QA should be a team exorcise for collaborative improvement, not a blame game
or for shaming.**

QA is part of a bigger process, and to make sense of it we have to see the
process as a whole. There are 3 types of units of work:

1. **Features**: Larger functional tasks, usually specified by _Jobs to be done_
   from the needs of a user. Features should have a list of acceptance criteria
   as a result of design work. But this can also be expanded as a part of the
   implementation.
1. **Tasks**: Smaller units of work derived from Features. One feature can
   result in several tasks, often technical in nature. A task has concrete
   deliverable (either by documentation, design work or development).
1. **Bugs**: Corrections, bugs or minor enhancements. This can be bugs reported
   from using a solution or a result of doing a task or QA. When performing
   tasks we can come across other technical or non-technical issues. These
   should either be solved as a part of the task (if integral for its
   completion) or added as a separate bug. A bug can be added as a part of a
   feature and task, or be standalone.

There are different levels of QA on the different unit of works, starting from
the bottom:

1. **QA of Bugs**: By the original reporter and/or developers/designers. Code
   review after Pull Request.
2. **QA of Tasks**: By using code reviews on Pull Requests.
3. **QA of Features**: Manual testing on a test version of the app when a
   Feature is marked as done (all Bugs and Tasks from that Feature is done).
4. **QA on releases**: General manual testing for regression issues.

In addition to the QA, there are automatic tests.

One important note is that QA doesn't prevent code from being merged to the
codebase. QA can produce new bugs, but not block code. It can block releases,
but only on critical bugs.

QA should be performed through Github issues and comments. All bugs should be
linked to base-feature which is undergoing QAs.

## Discussion

We should prefer exploration and real-world feedback for features over perfect
upfront planning and design. The QA process should reflect this prioritization.
The suggested implementation as summarized above and
[the QA progress guide](../guides/workflow-and-qa-progress-apps.md) reflects
this order of priority. Instead of having QA block tasks, we have it produce new
ones that can be individually prioritized.

QA can block releases when critical bugs are found. This can be bugs as
conceptually breaking something, or breaking universal design. QA should also be
used as a last check before periodic releases to production stores.

QA can often cause discussions on what is more important or uncover different
perspectives. These discussions are important for contexts and further work. To
keep all this important context, all communication on QAs should either be
through comments and issues on Github or summarized as comments/issues.
