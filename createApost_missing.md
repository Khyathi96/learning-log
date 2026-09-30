# LinkedIn "Create A Post" option missing in Chrome (AdGuard conflict)

Date resolved: 30 Sep 2026

## Problem

The schedule-for-later (clock) icon was missing in the LinkedIn post composer on desktop Chrome. It was visible on mobile and in Edge.

## Symptoms

Start a post opened the composer, but only the Post button showed, with no "Create a post" option.
The Premium subscription was Active, so the plan wasn't the cause.
A hard refresh didn't help.
Incognito worked, which pointed to a browser extension.

## Root cause

The Social widgets filter in the AdGuard AdBlocker extension (v5.5.2.54) was hiding the "Create a post" option. The filter targets Like and Share elements, and it matched the composer's scheduling button by accident.

## Diagnosis steps

Tested in Edge: worked, so the account was fine.
Tested in Chrome Incognito: worked, so an extension was the cause.
Turned off AdGuard: worked, so AdGuard was the extension.
Turned off AdGuard's filters one by one: Social widgets was the culprit.

## Fix

Open AdGuard Extension options → Allowlist.
Add linkedin.com on line 1 and click Save.
Keep the Allowlist toggle on.
Hard refresh LinkedIn (Ctrl+Shift+R) and reopen Start a post.

Result: the schedule icon appeared, and Social widgets stays on for all other sites.

## Prevention

If LinkedIn features go missing again, test in Incognito first. If it works there, suspect an extension.
AdGuard auto-updates its filters, so a rule change can break a site that worked yesterday. Keep linkedin.com in the allowlist.