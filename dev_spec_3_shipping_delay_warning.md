# Shipping delay warning — dev spec
Site: allbirds.com · Priority 3 · High · Effort: Medium (2-5 days)

## Problem
The prominent shipping delay notice on the homepage may deter immediate purchases by creating uncertainty about delivery timing.

## Evidence (from the live site)
> Body sample: 'Due to increased demand, orders may take up to 30 days to ship.'

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: The delay notice appears near the top of the page, potentially raising objections about delivery time.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Soften the message to 'Free shipping on orders over $100' and move the delay notice to a less prominent location, or add a reassurance like 'Most orders ship within 2-3 days' if accurate.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Soften the message to 'Free shipping on orders over $100' and move the delay notice to a less prominent location, or add a reassurance like 'Most orders ship within 2-3 days' if accurate.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_shipping_delay_warning` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
