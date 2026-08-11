# Vague hero copy — dev spec
Site: allbirds.com · Priority 2 · Urgent · Effort: Low (0.5-2 days)

## Problem
The hero headline and subhead are abstract and don't directly address the visitor's intent to find comfortable, sustainable shoes, causing them to rely on secondary content or navigation.

## Evidence (from the live site)
> H1: 'Wildly Comfortable. Super Natural.' CTAs: 'SHOP MEN' and 'SHOP WOMEN' with no subheadline visible in the crawl.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: No subheadline present; the hero is feature-led and doesn't mention the visitor's frustration (e.g., uncomfortable shoes, desire for sustainable options).

## Required change
h1: Shoes That Feel Like Nothing. Made From Nature.; cta: Shop Men / Shop Women; notes: Add a subheadline: 'Find your perfect fit for all-day comfort, made from sustainable materials.' This directly addresses comfort and sustainability, the brand's key differentiators.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Add a subheadline: 'Find your perfect fit for all-day comfort, made from sustainable materials.' This directly addresses comfort and sustainability, the brand's key differentiators.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_vague_hero_copy` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
