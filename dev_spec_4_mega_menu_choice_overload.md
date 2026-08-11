# Mega-menu choice overload — dev spec
Site: allbirds.com · Priority 4 · High · Effort: Medium (2-5 days)

## Problem
The mega-menu presents 20+ nav items with multiple sub-levels, risking choice overload and decision paralysis for users.

## Evidence (from the live site)
> nav_items list contains 20 items including 'New Arrivals', 'Shop All', 'Bestsellers', 'LEATHER ALTERNATIVES', 'Men's Shoes', 'Sneakers', 'Slip Ons', 'Sandals', 'Active', 'All-Weather', 'Runner NZ', 'Cruiser', 'Tree Runner NZ', 'Socks', 'Men's Apparel', 'Women's Shoes', 'Trainers', 'Flats', 'Canvas Cruiser', 'Women's Apparel'.

## Current state
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: The nav menu is dense with many categories and subcategories, potentially overwhelming users.

## Required change
h1: Wildly Comfortable. Super Natural.; cta: SHOP MEN / SHOP WOMEN; notes: Simplify the nav to top-level categories (e.g., Men, Women, Sale) with limited sub-items, or use a mega-menu with clear grouping and visual hierarchy to reduce cognitive load.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Simplify the nav to top-level categories (e.g., Men, Women, Sale) with limited sub-items, or use a mega-menu with clear grouping and visual hierarchy to reduce cognitive load.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_mega_menu_choice_overload` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 299,882 visitors per variant to detect a 5.0% relative lift
- Run at least one full business cycle; not testable at current traffic

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
