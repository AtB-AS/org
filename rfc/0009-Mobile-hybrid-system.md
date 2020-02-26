---
date: "2020-01-14"
author: Mikael Brevik <@mikaelbr>, Christian Brevik <@cbrevik>
---

# Mobile hybrid system

### Goals

- Avoid having too many codebases to maintain
- Avoid having to reimplement the same concepts for many platforms
- Allow developers to use their preferred development environment
- Ensure the end-user experience is idiomatic to their preferred platform.
- Be performant on both iOS and Android
- Have established developer tools for quick development and feedback loops.
- Allow for quick deploy
- Allow for A/B testing and user insight
- Be accessible and have tools for universal design
- The solution should durable and long-lived
- Should co-exist with the other parts of the architecture
- An ecosystem of learning material, bug fixes, community packages
- Degree of external adoption, access to external competency (community).
- Allow for an escape hatch to native code where necessary
- Explore hybrid solution

### Non-goals

- Choosing deploy routines or solutions (might be a consequence, but it is not a
  goal itself)
- Choosing hybrid vs native
- Choosing IDE (might be a consequence, but it is not a goal itself)
- Choosing programming language (might be a consequence, but it is not a goal
  itself)
- Application Architecture (state management, etc).
- Standardization on programming language or platform.
- Establishing de-facto immutable choice on technology.

## Summary

Prioritizing speed (time to marked/test), existing knowledge, and potential
symbyotic relationship with existing Entur apps we propose React Native as a
framework/platform for initial release.

## Details

### Alternatives

Given the scope of limiting to a hybrid solution, these alternatives are found
as the most relevant for the discussion.

- **Flutter**
- **React Native**
- **Xamarin**
- Cordova
- Ionic
- NativeScript

## Discussion

Using the goals of performance, build tools and ensuring platform's idiomatic
solution, we limit the realistic solutions to Flutter, React Native and Xamarin.

React Native and Flutter is more similar, than Xamarin. Xamarin supports more
platforms but is generally more low level.

To be able to move quickly in an early phase, test out concepts and iterate, we
think it is best to use something the team is familiar with and is a "safe
choice". We think it is best to use React Native but should take the time to
reevaluate within the end of March. There is also the aspect of Entur AS's
existing solutions which are in React Native.
