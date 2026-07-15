# Teardown Summaries

## Quick reference for all 7 teardowns

---

## 1. Blinkit: Recipe-to-Cart

**File:** `blinkit-teardown.html`
**Type:** 0-to-1 Feature Design
**Tag colour:** Orange

**One-line:** Design a Recipe Discovery tab that auto-maps recipe ingredients to Blinkit SKUs and adds them to cart in one tap.

**The core insight:** 2B+ monthly food video views on YouTube India with zero grocery integration. Users who watch a recipe video and want to cook it must manually search each ingredient on Blinkit — 8-12 searches for a single recipe. The gap between "I want to cook this" and "I have the ingredients" is enormous and unaddressed.

**North star:** 5% of orders include a Recipe-to-Cart basket within 3 months.

**Key metrics:**
- AOV: 1x → 1.8x (recipe orders have higher basket value)
- Items per order: 5-7 → 12+ items
- New user cohort conversion: recipe discovery as acquisition hook

**GTM:** Pilot with Punjabi and South Indian cuisine recipes (highest search volume in metros), then expand. Partner with food creators for recipe API integration. Measure AOV uplift in pilot cohort vs control.

---

## 2. Inshorts: Quality-First Feed

**File:** `inshorts-teardown.html`
**Type:** Recommendation System Redesign
**Tag colour:** Blue

**One-line:** Replace engagement-based feed ranking with a News Quality Score that weights credibility over clickbait, and tier notifications into Breaking / Daily Digest / Weekly Roundup.

**The core insight:** Inshorts' feed algorithm optimises for swipe volume, which amplifies clickbait at the expense of substantive news. Over time, this erodes user trust. The power users who came to Inshorts for quality, concise news are leaving for alternatives.

**North star:** DAU/MAU ratio rising from 42% to 48%+.

**Key metrics:**
- Notification open rate: 8-12% → 18%+
- D7 retention improvement
- NPS uplift among "quality-seeker" persona

**The NQS formula:** Source Credibility + Editorial Rating + Factual Density + Uniqueness + Timeliness — applied as a multiplier to engagement signals, not a replacement for them.

---

## 3. Khan Academy: Closing the Engagement Gap

**File:** `khan-academy-teardown.html`
**Type:** Growth & AI Strategy
**Tag colour:** Teal

**One-line:** Fix Khanmigo's activation problem (placement, not the AI itself) and build KAD Lite for international expansion.

**The core insight:** Only 11% of KAD-licensed students are Very Active Learners. Khanmigo, the AI tutor, sits idle because students don't know when or how to use it. The problem isn't the AI — it's that it requires students to proactively seek help, which most won't do. Embedding Khanmigo contextually into the practice flow (surfacing when a student struggles) would activate it without any change in student behaviour.

**North star:** Very Active Learners as % of KAD-licensed students: 11% → 20% in 6 months.

**Key metrics:**
- Khanmigo interaction rate: 5% → 30% of practice sessions with a struggle signal
- DAU/MAU: 15% → 25%
- KAD renewal rate: ~65% → 78%+

**International bet:** KAD Lite for India — mobile-first, offline-capable, $0.50/student/month. 250M school-going students, 0 current revenue from this market.

---

## 4. Supercell: Games People Play for Years

**File:** `supercell-teardown.html`
**Type:** Company Teardown (11 sections)
**Tag colour:** Amber/Gold

**One-line:** How a 300-person studio built a $10B+ mobile gaming empire by betting on retention over installs, and what the three-era strategy evolution tells us about durable product moats.

**The core insight:** Most mobile games are designed for install volume. Supercell bet against this — build games deep enough to play for years and the economics follow. 68% of Clash of Clans players came via word of mouth, not paid ads. This is only possible if the game is worth recommending.

**Three retention loops:**
1. **Daily habit** — resource timers force 4x/day return without feeling coercive
2. **Social obligation** — clan wars create accountability that no notification can replicate
3. **Progression milestone** — next Town Hall is always in sight (months away), giving players a clear goal

**Three-era strategy:**
- Build (2010–2016): Clash of Clans, Clash Royale — establish dominance
- Plateau (2016–2022): Struggle to launch new hits despite massive investment
- Reinvention (2023–present): Brawl Stars breaks out; Squad Busters attempted; new internal studio model

**PM lesson:** The strategy that gets you to the top is not the strategy that keeps you there.

---

## 5. Playo: Squad Mode

**File:** `playo-teardown.html`
**Type:** 0-to-1 Feature Addition
**Tag colour:** Green

**One-line:** Build "Squad Mode" — named groups of 3-8 players with recurring weekly slots, RSVP tracking, and a Smart Bench of fill-in players — to convert Playo from a booking tool into a sports habit.

**The core insight:** Playo's retention problem is social, not product. Every session is a fresh matchmaking event coordinated on WhatsApp, outside the app. Playo owns the booking but not the relationship. If the recurring play squad lives in WhatsApp, Playo has no stickiness.

**North star:** Monthly sessions per user: ~4 → 7+ sessions.

**Key metrics:**
- 30-day retention: 38% → 58%+
- Transactions per user per month (platform revenue)
- Squad formation rate in first 2 weeks of launch

**The Smart Bench:** When a squad member can't make it, they tap "I'm out." The bench — a list of compatible fill-in players — is auto-alerted. No WhatsApp scramble needed. This is the feature that makes the squad actually reliable.

---

## 6. Swiggy Instamart: Pantry Intelligence

**File:** `swiggy-teardown.html`
**Type:** Retention Mechanics
**Tag colour:** Amber

**One-line:** Build a pantry depletion model that predicts when staples will run out and sends proactive reorder notifications 3 days before depletion — reaching users before they open Blinkit or Zepto.

**The core insight:** In a market where all players deliver in 10 minutes, speed is table stakes, not a differentiator. Retention comes from switching costs. Swiggy One (the membership programme) is the structural moat — but the product must build the habit that makes the membership feel essential.

**North star:** Pantry reorder rate — % of predicted depletion events that result in a Swiggy Instamart order (vs competitor or physical store).

**The model:** Order history reveals consumption patterns. Milk ordered weekly → predict next order in 6-7 days → notify 3 days before predicted depletion. The user feels like Swiggy "knows" their household needs.

---

## 7. Duolingo: The Streak Economy

**File:** `duolingo-teardown.html`
**Type:** Engagement & Monetisation
**Tag colour:** Purple

**One-line:** Analyse how Duolingo's streak mechanic drives a 27% DAU/MAU ratio and propose a Proficiency Streak variant that's harder to game and better correlated with actual learning outcomes.

**The core insight:** Duolingo's DAU/MAU is built on loss aversion, not intrinsic motivation. Users open the app to protect their streak, not necessarily to learn. This is brilliant for engagement but creates a tension: the streak is gameable (Streak Freeze, minimal effort lessons) which undermines the product's core promise of language learning.

**The proposal:** A "Proficiency Streak" — consecutive days where the user completes exercises above their current difficulty floor. Harder to game with Streak Freeze (you have to actually perform). Better correlated with outcome metrics (proficiency test scores). Differentiates Duolingo from competitors who copy the basic streak mechanic.

**PM tension:** The current streak is a more reliable engagement driver. The proficiency streak is riskier short-term (some users will fail and churn) but better long-term (users who stick around are actually learning, reducing the "I paid for a year and learned nothing" churn trigger).
