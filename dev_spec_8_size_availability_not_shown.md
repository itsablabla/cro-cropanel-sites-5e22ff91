# Size availability not shown — dev spec
Site: allbirds.com · Priority 8 · High · Effort: Medium (2-5 days)

## Problem
Product pages do not display size availability upfront, forcing users to click through to select a size and potentially discover their size is unavailable, causing friction and potential abandonment.

## Evidence (from the live site)
> On the Anytime Ankle Sock product page, the CTA is 'Get Notified' instead of 'Add to Cart', indicating the product is out of stock, but the page does not show which sizes are unavailable until the user interacts with the size selector. The shop-all page includes a size filter, but individual product pages do not list available sizes in the main content.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: No size availability shown on the product page; users must click to see sizes and may find their size is not available.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Display available sizes and stock status directly on the product page, e.g., 'Sizes: S, M, L' or 'Out of stock' to reduce friction.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display available sizes and stock status directly on the product page, e.g., 'Sizes: S, M, L' or 'Out of stock' to reduce friction.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_size_availability_not_shown` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
