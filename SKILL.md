---
name: browser-operator
description: Reliable browser operation using Playwright MCP and structured browser tools.
---

# Browser Operator

Use this skill for website navigation, research, form interaction, downloads, account portals, browser tabs, and repetitive browser tasks.

## Preferred tool order

1. Prefer Playwright MCP structured browser tools.
2. Use browser snapshots before clicking.
3. Prefer element references, accessible names, links, buttons, and form controls over screen coordinates.
4. Use screenshots only when structured browser information is insufficient.
5. Use OpenMaus computer tools only for interfaces Playwright cannot operate.

## Operating loop

For every meaningful browser step:

1. Inspect the current page.
2. Identify the next target.
3. Take one meaningful action.
4. Inspect the resulting state.
5. Confirm the expected result occurred.
6. Continue.

Never assume a successful tool call means the intended webpage action succeeded.

## Navigation

Before navigating:
- verify which browser/profile/session is authorized;
- preserve the current login/session where possible;
- do not switch browser profiles without explicit permission.

When opening a link:
- prefer direct navigation when the destination URL is known;
- otherwise locate the correct visible link and activate it.

## Clicking

Never guess coordinates when a structured browser element is available.

Before clicking:
- confirm the target element label;
- confirm it belongs to the expected section of the page.

After clicking:
- inspect the new state;
- verify navigation, dialog appearance, selection change, or other expected result.

If the same click fails twice, stop repeating it and diagnose the problem.

## Forms

Before entering data:
- identify every required field;
- verify the correct record/account/page.

Fill fields deliberately.

Before submitting:
- review important values;
- ensure the submit action is intended.

After submitting:
- verify confirmation or resulting state.

## Tabs and windows

Track:
- active tab;
- page title;
- URL;
- task purpose for each relevant tab.

Do not act in unrelated tabs.

When opening new tabs, verify which tab became active before continuing.

## Downloads

When downloading:
- confirm the intended file;
- initiate the download once;
- verify completion;
- record the resulting filename/location when available.

Do not repeatedly trigger the same download.

## Login and verification

Preserve existing authenticated sessions.

If a site presents:
- CAPTCHA
- press-and-hold verification
- OTP
- MFA
- account verification
- suspicious-login verification

stop and request human completion.

After the user completes verification, inspect the page again and continue from the resulting state.

Do not repeatedly refresh or retry a verification challenge.

## Error recovery

If an action fails:

1. inspect the current page again;
2. determine whether the page changed;
3. identify whether the failure was caused by:
   - wrong element
   - stale element
   - navigation
   - popup/dialog
   - authentication
   - loading delay
   - site error
4. choose a different action.

Do not repeat the same failed action more than twice.

## Efficiency

Avoid unnecessary screenshots and repeated full-page reads.

Use structured snapshots to minimize token usage.

Keep an internal task state:
- objective
- current page
- completed steps
- next step
- blockers

Do not narrate every click unless asked.

## Completion

Before saying a browser task is complete, verify the requested end result directly.

Do not claim:
- a form was submitted,
- a file was downloaded,
- a login succeeded,
- a page was reached,
- or data was collected

unless the resulting browser state confirms it.
