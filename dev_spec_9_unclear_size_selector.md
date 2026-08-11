# Unclear size selector — dev spec
Site: allbirds.com · Priority 9 · High · Effort: Medium (2-5 days)

## Problem
The size selector on the product page may confuse users due to the presence of multiple size options and a note about half sizes, potentially leading to hesitation or abandonment.

## Evidence (from the live site)
> On /products/anytime-ankle-sock, the body sample includes 'Size Most of our shoes only come in full sizes. If you're a half size, select your nearest whole size too.' and the form labels include 'XS', 'S', 'M', 'L', 'XL', etc. The direct_signals show size_selector: true.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: The size selector is present but the guidance about half sizes may be unclear, and the CTA is 'Get Notified' (likely out of stock), which could frustrate users.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Clarify the size guidance with a tooltip or visual aid, and ensure the CTA reflects availability. If out of stock, provide a clear 'Notify Me' flow with expected restock date.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Clarify the size guidance with a tooltip or visual aid, and ensure the CTA reflects availability. If out of stock, provide a clear 'Notify Me' flow with expected restock date.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_unclear_size_selector` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
