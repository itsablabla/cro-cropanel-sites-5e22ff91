# Hidden shipping cost — dev spec
Site: allbirds.com · Priority 6 · Urgent · Effort: Medium (2-5 days)

## Problem
The product page shows a $10 price but does not disclose the $5 shipping fee or the $100 free-shipping threshold, leading to unexpected cost at checkout and potential cart abandonment.

## Evidence (from the live site)
> Product page prices list '$10' but no shipping information is visible in the body_sample; the homepage and collection pages show 'Free ground shipping on orders over $100' and 'Shipping $5.00' in the cart drawer, indicating a threshold that is not communicated on the product page.
> Homepage body sample: 'Free ground shipping on orders over $100' appears in the top bar, but the hero section and product pages do not mention this threshold. The cart drawer shows 'Spend more to earn free shipping! Shipping $5.00' without specifying the exact amount needed.

## Current state
h1: Anytime Ankle Sock; cta: Get Notified; notes: Price shown as $10, but no mention of shipping costs or free shipping threshold; 'Get Notified' suggests out-of-stock, further complicating the purchase path.

## Required change
h1: Anytime Ankle Sock; cta: Add to Cart (when in stock); notes: Display 'Free shipping on orders over $100' and note that shipping is $5 for orders below that, to set clear expectations before checkout.

## Acceptance criteria
- GIVEN a first-time visitor on the affected page
- WHEN the change is live
- THEN Display 'Free shipping on orders over $100' and note that shipping is $5 for orders below that, to set clear expectations before checkout.
- AND no layout regression at 375px / 768px / 1280px
- AND the changed control is keyboard-reachable with an accessible name

## Tracking
- Fire `cro_hidden_shipping_cost` on interaction with the changed element
- Verify the event fires in BOTH variants before opening traffic

## Test plan
- Two-proportion z-test, 95% significance, 80% power
- 118,817 visitors per variant to detect a 8.0% relative lift
- Run at least one full business cycle; 40 days

## Rollback
Feature-flag the change; revert if the primary metric drops for 3 consecutive days.
