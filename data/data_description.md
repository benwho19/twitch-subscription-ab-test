# Data Description

## Overview

This project uses two synthetic datasets that simulate a real-world A/B test on a live streaming platform similar to Twitch.

The data is structured to reflect the full lifecycle of an experiment:

* **Exposures** (treatment assignment and pre-exposure context)
* **Funnel outcomes** (post-exposure user behavior)

These datasets are designed to be joined at the **exposure level**, enabling causal analysis of treatment effects.

---

## Datasets

### 1. exposures

The `exposures` table represents each instance where a user is shown a Subscribe CTA.

Each row contains:

* treatment assignment (control vs. treatment)
* pre-exposure user context
* information used to determine microcopy

---

### 2. funnel

The `funnel` table captures user behavior after each exposure.

Each row contains:

* whether the user clicked the CTA
* whether they initiated checkout
* whether they subscribed (paid or Prime)
* guardrail-related outcomes

---

## Join Logic

The two datasets are joined to create a single analysis dataset at the **exposure level**.

Join keys:

* `user_id`
* `channel_id`
* `exposure_date`

In the full dataset, a stable row-level identifier (`exposure_id`) is used to guarantee a **one-to-one merge**.

---

## Data Generation

The datasets are synthetically generated to mimic a realistic A/B testing environment while maintaining full control over ground truth.

### Key assumptions

* Users are randomly assigned to control and treatment (≈50/50 split)
* Each user may have multiple exposures across time and channels
* Treatment increases conversion probability by approximately **10% relative**
* Behavioral features follow realistic, skewed distributions:

  * watch time
  * ad exposure
  * engagement signals
* Microcopy categories are assigned based on user context:

  * high ad exposure → ad-free messaging
  * high engagement → loyalty/perks messaging
  * fallback → creator support messaging

The goal is to simulate a realistic experimentation setting while ensuring interpretability and reproducibility.

---

## Data Dictionary

### exposures table

| Column             | Type     | Description                                             |
| ------------------ | -------- | ------------------------------------------------------- |
| user_id            | int      | Unique user identifier                                  |
| channel_id         | int      | Channel identifier                                      |
| exposure_date      | datetime | Date of Subscribe CTA exposure                          |
| experiment_variant | string   | Assigned variant (`control` or `treatment`)             |
| watch_minutes_7d   | float    | Total watch time in past 7 days                         |
| ads_seen_24h       | int      | Number of ads seen in past 24 hours                     |
| follows_channel    | binary   | Whether the user follows the channel                    |
| chatted_recently   | binary   | Whether the user recently chatted                       |
| is_prime_eligible  | binary   | Whether the user is eligible for Prime subscription     |
| microcopy_category | string   | Microcopy type shown (treatment only; null for control) |

---

### funnel table

| Column                | Type     | Description                                       |
| --------------------- | -------- | ------------------------------------------------- |
| user_id               | int      | Unique user identifier                            |
| channel_id            | int      | Channel identifier                                |
| exposure_date         | datetime | Join key with exposures                           |
| clicked_subscribe     | binary   | Whether user clicked Subscribe CTA                |
| checkout_started      | binary   | Whether user initiated checkout                   |
| subscription_type     | string   | Subscription outcome (`paid`, `prime`, or `none`) |
| low_intent_paid_proxy | binary   | Proxy for low-intent or refund-risk subscriptions |

---

## Sample Data

This repository will soon include a **small sample dataset** in the `data/` directory to allow the notebook to run end-to-end.

The sample:

* preserves schema and relationships between tables
* maintains realistic distributions
* is a subset of the full synthetic dataset

---

## Reproducibility

The full dataset is not included due to size and synthetic generation.

However:

* the (to-be-uploaded) sample dataset allows full execution of the analysis pipeline
* the schema and assumptions described here enable reconstruction of similar datasets

---

## Notes

* All data is **synthetic** and does not represent real users
* Column definitions and distributions are chosen to reflect realistic experimentation scenarios

---

## Summary

The data used in this project is structured to closely resemble a real-world A/B test, with clear separation between exposure context and outcome behavior. This enables rigorous analysis of treatment effects, while remaining fully synthetic and reproducible.
