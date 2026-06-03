---
layout: "../../layouts/BlogPost.astro"
title: "Toasts"
description: "Problems with one of the most common UI patterns, toasts"
pubDate: "June 3 2026"
---

I have been working on a design system and a general consensus has been established that toasts are bad UX and should be avoided. In this document I am going to talk about some potential alternatives and when, if ever, they could be used.

## What is a toast

[A toast in UI is a small, temporary notification that pops up on the screen to provide brief system feedback](https://open-ui.org/components/toast.research/).

The key characteristics of toasts:
- **Non-disruptive**: It appears in the corner or bottom of the screen, overlaying the content without blocking the user's workflow.
- **Self-dismissing**: It automatically vanishes after 3 to 8 seconds.
- **No user interaction required**: It is read-only and doesn't usually require the user to take action

## Why are they used everywhere

Mobile developers wanted a way to provide notifications to the user. They invented something to pop up from the bottom of the screen. Then there was a trend to align components for desktop and mobile applications, and thus toasts were suddenly available on ultra-wide monitors.

I personally think people love using toasts as it is a lazy solution for when an application needs to notify a user.

## What is the problem

These are the patterns toasts have that cause accessibility issues:
- Timing issues: users cannot read or interact with them before they disappear, or they appear on the screen in areas a user may not notice.
- Announcements: if not implemented correctly as live regions, content can be completely missed
- Distraction and layout shifts

## Alternatives

There is no catch all replacement, but heavily context dependent.

### Provide feedback near the trigger

Provide feedback next to the triggering element as users focus is already there. This is especially important for users who use screen magnification.

### Make the component dismissible

The notification should stay around until users take another action and users can dismiss it themselves.

## So, when is it ok to use?

I would see toasts accepting in the following situations:
- On specific mobile apps
- As a secondary, almost decorative, way to convey information. It is not bad to have redundant information conveying, but having it as the primary where it can easily be missed is a bad idea.