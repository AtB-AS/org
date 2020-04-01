# Workflow and QA progress in app development

This document describes flow for working with assignments on Github and how to
do quality assurance (QA) within that flow. Main goal of the flow is to:

1. have rapid development,
1. ensure we utilize our development capacity,
1. keep context and important discussion close to code and have it trackable
   over time,
1. and ensure general quality of solutions.

**QA and this flow is a team exorcise for collaborative improvement, not a blame
game or for shaming others. Our codebase, our problem our solutions.**

### Project setup

Work is split into sprints of 3 weeks. We should try to do releases after each
sprint.

Each sprint has different legs (see below for a description of the different
words):

1. **`To be defined`**: _Features_ that should be split into tasks or bugs that
   need more information to reproduce. Ordered by priority.
1. **`Ready for work`**: Tasks and bugs ready to be in progress. Ordered by
   priority.
1. **`In progress`**: Tasks and bugs in progress. Features with tasks in
   progress is also in progress.
1. **`QA`**: _(only Features)_ Features with all their tasks and bugs in `Done`
   column.
1. **`Done`**: Features undergone QA. Also tasks and bugs with PRs merged.

### Progress flow

Between each leg there's an activity moving it from one to another. Here is the
complete flow for tasks and bugs.

#### Tasks and bugs

1. **`To be defined`** → Split feature into tasks and describe. → **Ready for
   work**
1. **`Ready for work`** → Work starts. Open Draft Pull Request if code changes.
   → **`In progress`**
1. **`In progress`** → Add reviewer to PR. Do code review. Merge PR. Close
   related issues. → **`Done`**

#### Features

1. **`To be defined`** → All tasks specified and acceptance criteria specified.
   → **`Ready for work`**
1. **`Ready for work`** → One task or bug in progress → **`In progress`**
1. **`In progress`** → All tasks and bugs in `Done`. Clear assigned person on
   Feature card. Release new test version → **`QA`**
1. **`QA`** → Perform QA as specified below. → **`Done`**

All changes, comments and interjections should be performed through Github
issues and comments. All bugs should be linked to base-feature which is
undergoing QAs.

#### `QA` → `Done`

When Feature is moved from **`In progress`** to **`QA`**, we should send a
_Request for Quality Assurance_ on the `#qa` channel on the team Slack to
prevent tasks QA assignments from going stale. Ensure that a new version is
released to test stores (Test Flight and Alpha store).

Typical flow for performing QA on a Feature:

1. Validate all acceptance criteria on Feature card. Check if something should
   be changed or added.
1. Check that all sub tasks and bugs are closed and in done column.
1. Install latest version from alpha stores or test flight on your device and/or
   test devices.
1. Do general testing and check all acceptance criteria, marking them as done as
   you go.
1. If issue found:
   1. [Create new issue](https://github.com/AtB-AS/mittatb-app/issues/new/choose).
      - Add labels and assign someone if applicable.
   1. If critical:
      1. Add issue to project and prioritize it in **`Ready for work`** column.
      1. Edit description on the Feature issue, adding link to created card.
         Example: `- [ ] #125 - Bug title`
      1. Note the previously assigned person and leave a comment on the Feature
         issue.
1. If enhancement suggestion:
   1. [Create new issue](https://github.com/AtB-AS/mittatb-app/issues/new/choose).
      - Describe enhancment and say if this is `need-to-have` or `nice-to-have`,
        or simply just a request for comment/discussion.
1. When all acceptance criteria, tasks and bugs for a Feature is flagged as
   done:
   1. Check all checkboxes on issue
   1. Comment on summary (e.g. Looks good to me, good job, etc.).
   1. Close Feature
   1. Move Feature to `Done`
   1. Give mental high fives all around.

### Terms and glossery

There are 3 types of units of work used above:

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

---

### Template/example for Feature card with tasks, bugs and acceptance criteria

- **Label**: `Feature`
- **Projects**: Board of current sprint
- **Milestone**: (Optional) Part of larger goal

```md
## Motivation

When traveling we often need to know departures from nearby. This is typically
when standing at a quay and we want to see the next transportation from where we
are (or some place nearby).

## Tasks

- [x] #57
- [x] #58

## Bugs

- [x] #104

## Example

![Position](https://user-images.githubusercontent.com/606374/77403199-2aebf580-6db0-11ea-8ab2-cc7553706d83.png)

## Acceptance criteria

- [ ] Users should be able to to open and show nearby departures based on
      current location (if activated).
- [ ] If geolocation permission is not active, "Nearby screen" should show an
      input button to select place.
- [ ] Users should be able to specify where they are/want to search nearby
      departures from
- [ ] Users should be able to search for specific stops as well as other
      locations.
- [ ] Users should only see a service journey once, even if they are close to
      two stops that service journey crosses. Should see the closest stop.
- [ ] Users should see departures by time (meaning ordered by departure time)
- [ ] Users should get info on if the departure time is real-time.
- [ ] Users should be able to see a departures entire trip (all stops on that
      service journey).
```
