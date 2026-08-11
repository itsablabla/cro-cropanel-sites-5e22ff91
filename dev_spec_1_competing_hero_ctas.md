# Competing hero CTAs — dev spec
Site: allbirds.com · Priority 1 · Urgent · Effort: Medium (2-5 days)

## Problem
The hero presents two equally prominent CTAs (SHOP MEN and SHOP WOMEN) that split user focus and delay the path to a single product or category, reducing click-through to a defined next step.

## Evidence (from the live site)
> Hero section contains both 'SHOP MEN' and 'SHOP WOMEN' CTAs, with no primary/secondary hierarchy; body_sample shows 'SHOP MEN SHOP WOMEN' immediately after the headline.
> H1: 'Wildly Comfortable. Super Natural.' CTAs: 'SHOP MEN' and 'SHOP WOMEN' with no subheadline visible in the crawl.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN | SHOP WOMEN; notes: Two equal CTAs force an immediate gender choice, adding friction and potentially increasing bounce for undecided visitors.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: Shop All (primary) | Shop Men / Shop Women (secondary links); notes: A single primary CTA to 'Shop All' reduces decision load; gender-specific CTAs can be secondary links below.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN A single primary CTA to 'Shop All' reduces decision load; gender-specific CTAs can be secondary links below.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_competing_hero_ctas` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
