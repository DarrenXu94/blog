---
layout: "../../layouts/BlogPost.astro"
title: "Understanding disclosures, menus, comboboxes"
description: "Casual notes on disclosure, accordion, combobox, and menu patterns, focusing on accessibility and practical implementation tips."
pubDate: "May 30 2026"
---

Whilst working on design systems I have started developing a deeper understanding of some native web patterns. I'll try to document them all, starting with the general 'click button that expands other things' pattern.

## Disclosure

A [disclosure](https://webaim.org/techniques/disclosures/) is a simple pattern for showing or hiding content. It typically includes a trigger (usually a button) and a content area whose visibility the trigger controls.

You can implement a disclosure with a button plus JavaScript and ARIA, or you can use native HTML with `<details>` and `<summary>`.

Many more complex components are built on the disclosure pattern.

Disclosure basics:

- Triggers should be interactive elements — don't rely on non-interactive elements with `onclick`.
- Triggers must be focusable.
- Trigger labels shouldn't include state text; expose state via attributes like `aria-expanded`.
  - Ensure opening/closing is announced to assistive technologies.

## Accordions

Accordions are grouped disclosures, usually stacked vertically. The key difference is that only one section is open at a time.

You can create a basic accordion with multiple `<details>` elements, coordinating them so only one is expanded.

The accordion header button should have `aria-controls` pointing to the ID of the panel it toggles.

## Combobox

A combobox is an input with an associated popup. Patterns built from comboboxes include:
- Selects
- Autocompletes
- Datepickers

There are standard keyboard behaviors and roles for comboboxes. They cover many variations — see the [W3C APG combobox](https://www.w3.org/WAI/ARIA/apg/patterns/combobox/) page for details.


## Menu and menubar pattern

A [menu](https://www.w3.org/WAI/ARIA/apg/patterns/menubar/) is typically opened by a menu button; selecting an item may open a submenu. When a choice is activated, the menu usually closes unless it opened a submenu.

How menus differ from disclosures:

- Menus have specific keyboard behaviors.
- The menu container uses role `menu` or `menubar`.
- Menu items require appropriate roles:
  - `menuitem`
  - `menuitemcheckbox`
  - `menuitemradio`
- Manage `tabindex` so Tab doesn't move focus between menu items.


## Hide until functionality

A useful state to know is [hidden="until-found"](https://developer.mozilla.org/en-US/docs/Web/HTML/Reference/Global_attributes/hidden#the_hidden_until_found_state). In this state the element is hidden but its content is still discoverable by the browser's Find-in-page or fragment navigation.

I often notice component libraries skip this, which matters for components like accordions (see [Radix UI](https://www.radix-ui.com/primitives/docs/components/accordion)).