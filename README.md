# Improving Twitch Subscription Conversion with Contextual Microcopy (A/B Test)

## Overview

This project simulates an end-to-end product experiment to improve paid subscription conversion on a live streaming platform similar to Twitch.

Viewers often hesitate to subscribe because the value of subscribing (ad-free viewing, perks, or supporting creators) is not always clear at the moment of decision. This experiment tests whether **contextual value microcopy** shown under the Subscribe CTA can reduce friction and increase conversions.

---

## Product Context

Twitch is a live streaming platform where users can subscribe to creators for benefits such as:
- Ad-free viewing
- Custom emotes and badges
- Supporting creators directly

Subscriptions can be paid or included through Prime membership. Despite these benefits, subscription conversion rates are low, suggesting friction in communicating value.

---

## Experiment Design

### Hypothesis
Adding contextual value microcopy under the Subscribe CTA will increase paid subscription conversion by making the value of subscribing more salient at the decision moment.

### Variants
- Control: Standard Subscribe CTA  
- Treatment: Subscribe CTA + contextual value microcopy

Microcopy is tailored based on user context:
- High ad exposure → emphasize ad-free viewing  
- High engagement → emphasize loyalty/perks  
- Fallback → emphasize creator support  

### Key Details
- Unit of randomization: user-level  
- Population: logged-in users not already subscribed  
- Primary metric: paid subscription conversion rate (same-day)  
- Guardrails: engagement (watch time, chat), monetization (ads), quality (low-intent purchases)

---

## Key Results

- **+10% relative lift** in paid subscription conversion (0.50% → 0.55%)  
- Statistically significant improvement (p < 0.001)  
- Consistent gains across the funnel:
  - Subscribe clicks ↑  
  - Checkout starts ↑  
  - Total subscriptions ↑  
- **No meaningful negative impact** on:
  - Watch time  
  - Chat engagement  
  - Ad impressions  
  - Subscription quality  

---

## Methodology

This project demonstrates a full experimentation workflow:

- A/B test design and metric selection  
- Power analysis and sample size estimation  
- Two-proportion z-tests and confidence intervals  
- Logistic regression with clustered standard errors  
- Guardrail analysis for risk assessment  
- Segmentation analysis and interaction modeling  

---

## Segmentation Insights

Treatment effects were directionally stronger for **Prime-eligible users**, suggesting that contextual microcopy is particularly effective at helping users recognize and activate existing subscription benefits.

- Larger lift in overall subscriptions for Prime users  
- Paid subscription lift consistent across segments  
- Interaction model suggests heterogeneity but is not statistically conclusive  

Insight: Microcopy appears especially effective at surfacing latent value, not just driving new purchases.

---

## Final Recommendation

Ship to 100% of users.

The treatment produces a meaningful increase in paid conversions without harming engagement or monetization, and results are robust across multiple analyses.

---

## Next Steps

- Personalize microcopy based on user context (e.g., Prime eligibility, engagement)  
- Optimize messaging variants (A/B/n testing)  
- Experiment with CTA design and placement  
- Evaluate long-term retention and lifetime value impact  

---

## Repository Structure

- notebook/ — full analysis notebook  
- data/ — simulated dataset  
- images/ — visualizations  

---

## How to Run

pip install -r requirements.txt

Open the notebook and run all cells.

---

## Takeaways

This project demonstrates how thoughtful experimentation and behavioral framing can meaningfully improve conversion in a product setting while maintaining user trust and experience.
