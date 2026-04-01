# Experiment Design Doc: Improving Subscription Conversion with Contextual Microcopy

## 1. Objective

Increase paid subscription conversion by improving how value is communicated at the moment users decide whether to subscribe.

---

## 2. Background & Motivation

On live streaming platforms like Twitch, users can subscribe to creators for benefits such as ad-free viewing, exclusive perks, and direct support. However, subscription conversion rates are low, suggesting that users may not fully understand or recognize the value of subscribing at the point of decision.

In particular, some users (e.g., Prime-eligible users) already have access to subscription benefits at no additional cost, but may not realize this when interacting with the Subscribe CTA.

---

## 3. Hypothesis

Adding contextual value microcopy under the Subscribe CTA will increase subscription conversion by making the value of subscribing more salient and reducing decision friction.

We expect the effect to be especially strong among users with latent value (e.g., Prime-eligible users), where the barrier is awareness rather than price.

---

## 4. Experiment Design

### Variants

- Control: Standard Subscribe CTA  
- Treatment: Subscribe CTA + contextual value microcopy  

### Microcopy Logic

Microcopy is dynamically selected based on user context:

- High recent ad exposure → emphasize ad-free viewing  
- High engagement (e.g., follows, chat) → emphasize loyalty and perks  
- Fallback → emphasize supporting creators  

---

## 5. Unit of Randomization

- User-level randomization

Each user is assigned to either control or treatment and remains in that variant throughout the experiment.

---

## 6. Target Population

- Logged-in users  
- Not currently subscribed to the channel  
- Eligible to see the Subscribe CTA  

---

## 7. Metrics

### Primary Metric

- Paid subscription conversion rate (same-day)  
  - Definition: proportion of exposures that result in a paid subscription on the same day  

---

### Secondary Metrics (Funnel Diagnostics)

- Subscribe CTA click-through rate  
- Checkout initiation rate  
- Prime subscription rate  
- Any subscription rate (paid or Prime)  

---

### Guardrail Metrics

To ensure no unintended harm:

- Engagement
  - Watch time (minutes)
  - Chat activity

- Monetization
  - Ad impressions

- Quality
  - Low-intent paid subscription proxy (refund/chargeback risk)

---

## 8. Success Criteria

The experiment will be considered successful if:

- Paid subscription conversion shows a statistically significant increase  
- The effect size is practically meaningful (e.g., ≥ ~10% relative lift)  
- No meaningful degradation in guardrail metrics  

---

## 9. Power Analysis & Sample Size

- Baseline conversion rate: ~0.5%  
- Minimum detectable effect (MDE): +10% relative lift  
- Significance level: α = 0.05  
- Power: 80%  

Estimated required sample size:
- ~327,000 exposures per variant  

---

## 10. Risks & Assumptions

### Risks

- Microcopy may distract users or create cognitive overload  
- Increased subscriptions could reduce ad impressions (revenue tradeoff)  
- Potential increase in low-intent or impulsive subscriptions  

---

### Assumptions

- Users respond to clearer value communication  
- Contextual messaging aligns with user intent  
- Same-day conversion captures meaningful behavioral impact  

---

## 11. Analysis Plan

- Compare conversion rates between treatment and control  
- Estimate lift (absolute and relative)  
- Conduct two-proportion z-tests and confidence intervals  
- Validate results using logistic regression with clustered standard errors  
- Evaluate guardrails for unintended effects  
- Conduct segmentation analysis (e.g., by Prime eligibility) to explore heterogeneity  

---

## 12. Interpretation Strategy

- Focus on both statistical significance and practical impact  
- Use confidence intervals to assess uncertainty  
- Treat segmentation results as exploratory unless formally validated  

---

## 13. Expected Outcomes

We expect:

- Increased paid subscription conversion due to clearer value communication  
- Stronger effects among users with latent value (e.g., Prime eligibility)  
- No meaningful negative impact on engagement or monetization  

---

## 14. Follow-Up Opportunities

- Personalization based on user context (eligibility, engagement)  
- Optimization of microcopy variants (A/B/n testing)  
- UI/UX improvements to CTA placement and prominence  
- Evaluation of long-term retention and lifetime value  

---

## 15. Summary

This experiment tests whether contextualizing value at the point of decision can meaningfully improve subscription conversion. By aligning messaging with user context, we aim to reduce friction, increase clarity, and drive higher-quality conversions without harming user experience.
