---
layout: "../../layouts/BlogPost.astro"
title: "Why do disabled states exist"
description: ""
pubDate: "10 June 2026"
---

The `disabled` pattern is widely used online, from buttons to form inputs. Most design systems components have a disabled prop. I never questioned this before until I started working with some accessibility specialists. After talking through the issues, I can't think of a scenario I would use them.

Here are the issues associated with the `disabled` property:

- `Poor contrast`: For some reason WCAG doesn't require disable elements to have correct colour contrast. This would require disable elements to be treated as decorative, which is usually never the case for where they are used.

- `Unclear as to why`: Disabled elements make people have to think about why it's disabled. What might be obvious to the designer/regular user may not be for everyone. 

- `Screen reader usability`: Disabled elements can't get focus so users navigating with keyboard will never know the element is there. Unless specifically designed for, they are also skipped by screen readers.

## What we can do instead

### Readonly and aria-readonly

Most cases of disabled should actually be `read-only`. Read-only has all the intended benefits from disabled and minimises much of the flaws. 

- allows focus but not editing. This way screen readers have the same experience as sighted users.
- allows text highlighting for copy and pasting
- still allows interactivity so you can add inline tooltips as to why an interaction in unavailable

The catch with `read-only` is that it only only works on inputs. We need to use aria-readonly for others use cases. eg checkboxes

### Don't use disabled as a gate

We can use error validation instead of gating - don't grey out the submit button if it's invalid. Let them submit and give the relevant errors. This prevents users having to guess which inputs need to be filled before they can continue.

### Display the content instead

Instead of showing an input which is disabled, can that information be disabled another way? eg. If a user sees an input with their ID which cannot be edited, does this need to be a form input in the first place? Can this information be displayed as text or label somewhere else. Instead of using `input disabled` can you use a `p` instead?

### Consider if it needs to be shown

Consider the reason and element is being disabled. Is it required to be on the page to convey some information or is it lazy coding? eg. If a previous page isn't available, don't show the button.

References

https://zeroheight.com/blog/rethinking-the-disabled-norm/

https://www.smashingmagazine.com/2021/08/frustrating-design-patterns-disabled-buttons/


