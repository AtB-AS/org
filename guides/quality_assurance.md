# Quality Assurance

This document describes the Quality Assurance (QA) process applied within the 
development processes for the AtB webshop on desktop and AtB mobile application.
The overall strategy is to:
1. Ensure that a (new or changed) functionality meets its acceptance criteria
1. Ensure that the functionality do not present any regression error
1. Ensure that the functionality is according to the accessibility requirements defined
by [Web Content Accessibility Guidelines (WCAG) 2.0](https://www.w3.org/TR/WCAG20/)

The QA process differ slightly between the AtB webshop and AtB mobile application
in terms of how the development process is defined and which tools are essential.
- [QA in AtB webshop](#qa-in-atb-webshop)
- [QA in AtB mobile application](#qa-in-atb-mobile-application)


## QA in AtB webshop

The AtB webshop is a single-page application mainly developed for desktops, but should
also be usable from mobile terminals like pads and phones. This must therefore be
reflected in the QA process of verifying the features and changes.

### Devices, browsers and tools

There is a range of browsers and operating systems available, and such not feasible to cover
all available. Therefore, the execution of the QA process is focusing on a few main OS and browsers - 
with the small possibility of missing out on a small percentage of the users:

- Desktops
    - Use your own OS
    - Evergreen browsers, most notably Chrome, Safari, Firefox and Edge
- Mobile devices
    - iOS: Safari and Chrome
    - Android: Chrome
- Accessibility
    - VoiceOver on iOS
    - Talkback on Android
    - WAVE extension to Chrome and Firefox
    - W3C validator

### Process transitions

- [`QA of PRs`](#qa-of-prs)
- [`QA` → `QA approved`](#qa--qa-approved)
- [`QA approved` → `Done`](#qa-approved--done)

#### `QA of PRs`

TODO This is a more simplified QA step than the one described for the transition `QA` → `QA approved`.
It involves mainly the same steps, but one can limit the functional tests to only
a few of the OS and browsers mentioned. A more thorough QA is applied when the Issue
the PR represents reaches the `QA` phase.

#### `QA` → `QA approved`

When an Issue is moved from `In progress` to `QA`, it means that the Issue (Feature, 
Improvement, Fix) is available for QA in out test environment (i.e. staging).

Typical flow for performing QA on an Issue:

1. Assign yourself to the Issue.
1. Verify that the description is well understood, and includes necessary information
   for the QA
1. Validate all acceptance criteria on the Issue. Check if something should be
   changed or added. Bug fixes may have fewer criteria than Features as the observed
   error no longer should appear.
    1. Functional testing for desktop: Do general testing according to description and acceptance 
   criteria. Repeat the tests across all browsers mentioned if not a specific browser is
   mentioned. 
    1. Functional testing mobile device: Do general testing according to description and acceptance
   criteria. Repeat the tests across all OS and browsers mentioned. Pay extra attention to
   how the implementation has affected the mobile viewport.
    1. Accessibility: Do a quick check by using the WAVE extension in Chrome/Firefox. Use
   VoiceOver and Talkback to look for accessibility issues as more described in [Accessibility](#accessibility)
1. If an issue is found: 
    1. [Create new issue](https://github.com/AtB-AS/webshop/issues/new/choose).
        - Add labels and assign someone if applicable.
    1. If critical:
        1. Add issue to project and prioritize it in **`Ready for work`** column.
        1. Edit description on the Feature issue, adding link to created card.
           Example: `- [ ] #125 - Bug title`
        1. Note the previously assigned person and leave a comment on the Feature
           issue.
1. If enhancement suggestion:
    1. [Create new issue](https://github.com/AtB-AS/webshop/issues/new/choose).
        - Describe enhancment and say if this is `need-to-have` or `nice-to-have`,
          or simply just a request for comment/discussion.
1. When all acceptance criteria, tasks and bugs for a Feature is flagged as
   done:
    1. Check all checkboxes on issue
    1. Comment on summary (e.g. Looks good to me, good job, etc.).
    1. Move Feature to `QA approved`
1. Unassign yourself from Feature

#### `QA approved` → `Done`

Normally, this transition is done on an ad-hoc basis without the need for any explicit QA. In
some circumstances there might, however, be a need for a round of QA before going to production.
This typically depends on which functionality is to be released, and the size of the release. In
later stages of the project there will be a need for a more holistic _acceptance test_ without 
the more Issue centric QA view in previous phases. One aspect here is to include more members
from the team - or organization - to get a broader view on the new release. The following steps
should be carried out:
1. Walk-though of the application functionality on desktop
    1. Does everything play together
    1. Not-affected functionality still works as intended
    1. Is the design as intended
1. Walk-through of the application functionality on mobile devices with accessibility tools
1. Buy a ticket
   1. Attach a travel card to the account
   1. Control the travel card on an available control unit


## QA in AtB mobile application

The AtB mobile application is developed for both iOS and Android, and available through
AppStore and PlayStore, respectively. This must therefore be reflected in the QA process
of verifying the features and changes.

### Devices and tools

There is a range of iOS and Android versions in use, and such not feasible to cover all 
available. It is therefore, especially for the testing phase `Kan testes i TestFlight`
(eng: `Able to test in TestFlight`), valuable to have devices with different versions
of iOS and Android. For the other phases it is good enough to have an iOS and Android
device, and have the Android emulator and iOS simulator available for verification of
issues - especially issues that requires specific versions.

- Mobile devices
    - iOS
    - Android
- Accessibility
    - VoiceOver on iOS
    - Talkback on Android

### Process transitions

- [`QA during development`](#qa-during-development)
- [`Utvikling pågår` → `Kan testes i staging`](#utvikling-pgr--kan-testes-i-staging)
- [`Klart for TestFlight` → `Kan testes i TestFlight`](#klart-for-testflight--kan-testes-i-testflight)
- [`Kan testes i TestFlight` → `Done`](#kan-testes-i-testflight--done)
- [`Done`](#done)

#### `QA during development`

`QA during development` is a more simplified QA step than the QA in phase 
`Kan testes i staging`. It involves mainly the same steps, but one can limit the functional
tests to an Android emulator or iOS simulator. Accessibility issues should be covered
by the emulator's or simulator's text-to-speech functionality. Testing on real devices 
are left to the `Kan testes i staging` phase.

#### `Utvikling pågår` → `Kan testes i staging`
(eng: `In progress` → `Available in staging`)

When an Issue is moved from `Utvikling pågår` to `Kan testes i staging`, it means that the
Issue (Feature, Improvement, Fix) is available for QA in out test environment (i.e. staging).

Typical flow for performing QA on an Issue:

1. Assign yourself to the Issue.
1. Verify that the description is well understood, and includes necessary information
   for the QA
1. Ensure that the new staging version is available for both iOS and Android in [appcenter](https://install.appcenter.ms). 
   Download these to an iPhone or Android device, respectively.
1. Validate all acceptance criteria on the Issue. Check if something should be
   changed or added. Bug fixes may have fewer criteria than Features as the observed
   error no longer should appear.
    1. Functional testing on iOS: Do general testing according to description and acceptance 
       criteria. Pay extra attention to language and looks if the issue affects these. Also pay
       attention to any side effects of the changes.
    1. Functional testing on Android: Do general testing according to description and acceptance
       criteria. Pay extra attention to language and looks if the issue affects these. Also pay
       attention to any side effects of the changes.
    1. Accessibility: If applicable, use VoiceOver and Talkback to verify and look for
       accessibility issues as more described in [Accessibility](#accessibility)
1. If an issue is found:
    1. [Create new issue](https://github.com/AtB-AS/mittatb-app/issues/new/choose).
        - Add labels and assign someone if applicable.
    1. If critical:
        1. Add issue to project and prioritize it in **`Backlog`** column.
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
    1. Move Feature to `Klart for TestFlight` (eng: `Ready for TestFlight`)
1. Unassign yourself from Feature

#### `Klart for TestFlight` → `Kan testes i TestFlight`
(eng: `Ready for TestFlight` → `Available in TestFlight`)

This is a transition that indicates when a new version is released to TestFlight. No QA is
done on this transition - it is merely a release step.

#### `Kan testes i TestFlight` → `Done`
(eng: `Available in TestFlight` → `Done`)

Before releasing a new version to production, i.e. Google's PlayStore for Android and Apple's 
AppStore for iOS, a new round of QA is performed on the versions available in TestFlight (iOS)
and alpha/beta-channels of PlayStore. Before starting on the QA in TestFlight, ensure that the version
is available and ready for download and install.

The QA in this phase is two-fold: Issue centric and holistic.

**Issue centric**

The process mainly follows the steps defined for the `Kan testes i staging` phase, but testing of
each Issue is a bit more brief due to the thorough QA done in previous phases. However, each Issue
should undergo:
1. Functional testing on iOS: Do general testing according to description and acceptance
   criteria. Pay extra attention to language and looks if the issue affects these. Also pay
   attention to any side effects of the changes.
1. Functional testing on Android: Do general testing according to description and acceptance
   criteria. Pay extra attention to language and looks if the issue affects these. Also pay
   attention to any side effects of the changes.
1. Accessibility: If applicable, use VoiceOver and Talkback to verify and look for
   accessibility issues as more described in [Accessibility](#accessibility)
1. If an issue is found, create a new issue, or comment on the existing, and then notify the 
   developers on the dedicated Slack-channel for QA in Testflight.
1. When all acceptance criteria, tasks and bugs for a Feature is flagged as done, mark the issue
   with the label `TestOK`. The Issue is moved to the next phase (i.e. `Done`) when the version
   is released into production.
   
**Holistic**

When all Issues are labelled `TestOK`, the whole application should be tested without specific
regards to the Issues included in this version. This test should be carried out by several members
of the team - or beta testers with access to the TestFlight release. The following steps should
be carried out:
1. Walk-though of the application functionality
    1. Does everything play together
    1. Is the design as intended
    1. Do change in the settings deploy throughout the application
1. Walk-through of the application functionality with accessibility tools
1. Buy a ticket and control the ticket on an available control unit (both Android and iOS)
1. Test information and alert messages pushed to the app from Firebase

#### `Done`

After release to production, a last resort of verification should be applied:
1. Walk-through of the application functionality
1. Buy a ticket and control the ticket on an available control unit (both Android and iOS)

### Accessibility

_TBD How to test accessibility_
