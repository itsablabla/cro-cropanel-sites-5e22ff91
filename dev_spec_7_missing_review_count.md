# Missing review count — dev spec
Site: allbirds.com · Priority 7 · High · Effort: Medium (2-5 days)

## Problem
The product page lacks a visible review count, which may reduce trust and increase hesitation for first-time buyers.

## Evidence (from the live site)
> H2s include 'Reviews for Anytime Ankle Sock' but no review count or rating is visible in the extracted content.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: The page shows a reviews section but no aggregate rating or count, missing an opportunity to leverage social proof.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart; notes: Add a review summary near the price, e.g., '4.8/5 from 2,300+ reviews' to build trust at the point of purchase.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a review summary near the price, e.g., '4.8/5 from 2,300+ reviews' to build trust at the point of purchase.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_missing_review_count` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
