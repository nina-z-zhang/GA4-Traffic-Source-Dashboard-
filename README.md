# GA4-Traffic-Source-Dashboard-
Used Google Merch Shop Demo Data to build a dashboard on Looker Studio for a marketing or growth team that needs to quickly understand channel quality, identify where to invest or cut spend, and monitor whether conversion trends are healthy.

**Tools:** Looker Studio · Google Analytics 4 (GA4) · Google Merch Shop Demo Data  
**Live Dashboard:** [View on Looker Studio](https://datastudio.google.com/reporting/ea37a056-df62-44dd-a779-a45d0baa93c9)  
**Period analysed:** April 2 – May 1, 2026

---

## Project Objective

The Google Merch Shop is growing fast — sessions are up 43% and total users up 62% compared to the prior period. But here's the problem: engagement rate has dropped 39.9% and average engagement time has fallen too. That gap between traffic growth and engagement quality is the core business tension this project investigates.

**The question isn't just "where is the traffic coming from?" — it's "which channels are actually worth it?"**

This dashboard is built for a marketing or growth team that needs to quickly understand channel quality, identify where to invest or cut spend, and monitor whether conversion trends are healthy — all without running a new query every time.

---

## Business Questions (KPIs)

1. **Which channels drive the most traffic — and which drive the most engaged, converting users?** (Volume vs. quality tradeoff)
2. **What is the revenue contribution of each channel, and which paid channels deliver the best ROI?** (Paid Search vs. organic benchmarks)
3. **Is new user acquisition growing faster than retained user engagement?** (Acquisition health over time)
4. **Which landing pages are the strongest entry points into the purchase funnel?** (Page-level conversion efficiency)
5. **How are overall conversions trending — and do traffic spikes translate into conversion spikes?** (Volume vs. intent alignment)

---

## Dashboard

<img width="2500" height="3645" alt="GA4_Traffic_Source_Dashboard" src="https://github.com/user-attachments/assets/1ae94ce9-22cf-4175-b0c2-27ffea1012c9" />

> 🔗 [Link to Interactive Dashboard](https://datastudio.google.com/reporting/ea37a056-df62-44dd-a779-a45d0baa93c9)

---

## Dashboard Design — What I Built & Why

### Controls & Filters
The dashboard opens with three interactive filters: **Session Default Channel Group**, **Device Category**, and a **Date Range picker**. These are not decorative — they power the cross-filtering logic that makes the entire dashboard reactive. A marketing analyst can click "Paid Search" in the donut chart or filter by "Mobile" in the dropdown and every single chart and table updates instantly. This means one dashboard serves multiple use cases: a channel owner auditing their own traffic, a manager doing a device breakdown, or an exec checking a specific date window.

### Scorecards — The 30-Second Health Check
The five scorecards at the top (Sessions, Total Users, Engagement Rate, Avg. Engagement Time, Conversions) are designed to answer "are we healthy?" in under 30 seconds. Each card includes a sparkline trend and a percentage change vs. the prior period. I deliberately included both volume metrics (Sessions, Users) *and* quality metrics (Engagement Rate, Avg. Time) side-by-side because they tell opposite stories in this dataset — and that tension is the core insight. A dashboard that only shows sessions would mask a serious engagement problem.

### Donut Chart — Top Channels by Users
The donut gives an immediate visual of channel share. I chose a donut over a bar chart here because the goal is proportional comparison, not absolute ranking — and because it doubles as a filter control. Clicking any slice cross-filters the entire dashboard to that channel only. The near-equal slice distribution (~10% each for most channels) also flags something important: no single organic channel dominates, which means Direct traffic is artificially inflating the share.

### Time Series — Users vs. New Users & Conversions (Separate Charts)
I split these into two separate time series rather than one combined chart. The **Users vs. New Users** chart tracks acquisition health — are we growing the base or just re-engaging the same people? The **Conversions** chart tracks purchase intent independently. Keeping them separate makes it easier to spot divergence: a traffic spike that doesn't produce a conversion spike is a signal problem (wrong audience), not a volume problem.

### Channel Performance Table — Acquisition + Behavior + Conversions in One View
This is the analytical core of the dashboard. I structured it across three column groups — Acquisition (Sessions, Active Users, New Users), Behavior (Engagement Rate, Views per Session, Avg. Engagement Time), and Key Events/Conversions (Key Events, Purchase Revenue) — because that mirrors the actual marketing funnel. You can see not just who shows up, but how they behave, and whether they convert. Conditional formatting highlights high values in blue and low values in yellow, making underperformers visually obvious without needing to sort manually.

### Landing Page Performance Table
The bottom table answers a different question: not which channel brought the user, but which page they landed on and how engaged they were. This is critical for UX and paid campaign teams — it shows where ad traffic should point, which organic pages are already high-performing, and where the homepage is leaking users.

---

## Business Insights — Answering the Questions

> 💡 Each insight includes a **How I got here** section showing exactly which table or chart I looked at and what calculations I ran — so you can verify or replicate the logic directly in the dashboard.

---

### 1. Volume ≠ Quality: Direct Traffic Is Dominating — But It Shouldn't Be
Direct traffic accounts for **71,505 sessions (66% of all traffic)**, generating the most revenue in absolute terms ($97,542). But its engagement rate is only **22.6%** and average engagement time is just 37 seconds — the worst of any meaningful channel. This means the majority of sessions are low-intent: people landing and leaving quickly, possibly from bookmarks, dark social, or misattributed sources. Direct is the biggest channel by volume but the weakest by quality. The traffic surge (+43% sessions) is largely driven by Direct, which explains why overall engagement rate dropped 39.9% even as total volume grew — more traffic, but most of it shallow.

<details>
<summary>📊 How I got to this insight</summary>

**Where I looked:** Channel Performance table — Sessions column and Engagement Rate column.

**Calculation 1 — traffic share:**
- Direct sessions ÷ Grand total sessions = 71,505 ÷ 107,711 = **66%**

**Calculation 2 — key events per session (quality check):**
- Direct: 39,881 key events ÷ 71,505 sessions = **0.56 key events per session**
- This means the average Direct session doesn't even complete one tracked action

**Observation:** Scanning the Engagement Rate column row by row, Direct sits at 22.6% while every other meaningful channel is above 60%. That contrast is immediate and flags Direct as a low-quality traffic source despite its volume dominance.

</details>

---

### 2. Organic Search Is the Highest-Quality Scalable Channel
With 16,690 sessions, **68.3% engagement rate**, and $31,975 in revenue, Organic Search is the clearest candidate for investment. It brings qualified users who actually explore the site (3.93 views/session, 1:00 avg engagement time). Crucially, Organic Search users generate more key events *per session* than any other high-volume channel — meaning they don't just visit, they act. Growing SEO content and optimising for commercial keywords should be a priority.

<details>
<summary>📊 How I got to this insight</summary>

**Where I looked:** Channel Performance table — Organic Search row, across all columns.

**Calculation 1 — key events per session:**
- Organic Search: 19,530 key events ÷ 16,690 sessions = **1.17 key events per session**
- Direct (for comparison): 39,881 ÷ 71,505 = **0.56 key events per session**
- Organic Search users complete **2× more tracked actions per session** than Direct users

> **Important GA4 note:** Key events in GA4 are counted at the event level, not the session level. One session can fire multiple key events (e.g. add_to_cart + begin_checkout + purchase each count separately). This is why key events (19,530) can exceed sessions (16,690) for this channel — it's not an error. It's actually a signal of high intent.

**Calculation 2 — revenue per session:**
- Organic Search: $31,975 ÷ 16,690 = **$1.92 per session**
- vs Direct: $97,542 ÷ 71,505 = **$1.36 per session**
- Organic Search earns more per session despite having no ad spend behind it

</details>

---

### 3. Paid Search Has the Best Revenue-Per-Session Ratio Among All Channels
Paid Search drives only 3,250 sessions but generates **$19,385 in revenue** — the highest revenue efficiency of any channel. Its engagement metrics are solid too (62.2% engagement rate, 1:13 avg engagement time), confirming it is capturing high-intent buyers, not just casual browsers. The question for the marketing team is whether the current budget is too conservative — this channel has clear room to scale.

<details>
<summary>📊 How I got to this insight</summary>

**Where I looked:** Channel Performance table — Paid Search row, Purchase Revenue and Sessions columns.

**Calculation — revenue per session across channels:**

| Channel | Sessions | Revenue | Revenue/Session |
|---|---|---|---|
| Paid Search | 3,250 | $19,385 | **$5.96** |
| Organic Search | 16,690 | $31,975 | $1.92 |
| Referral | 2,523 | $11,020 | $4.37 |
| Direct | 71,505 | $97,542 | $1.36 |
| Email | 343 | $2,087 | $6.09 |

Paid Search ranks among the top channels for revenue per session, with only Email slightly ahead — and Email has 9× fewer sessions, making it far harder to scale. Paid Search is the most actionable high-ROI lever.

</details>

---

### 4. Email Is the Highest-Intent Channel — But Almost Invisible
Email has only 343 sessions, but its metrics are remarkable: **76.7% engagement rate, 1:57 average engagement time, 6.65 views per session** — the highest of any channel across all three behaviour metrics. Email users are clearly the most motivated visitors. The issue is pure volume — the email list or send frequency is severely underutilised relative to its potential. A 10x increase in email sends, if list quality holds, would be a high-ROI lever.

<details>
<summary>📊 How I got to this insight</summary>

**Where I looked:** Channel Performance table — scanned the Engagement Rate, Avg. Engagement Time, and Views per Session columns from top to bottom across all rows.

**Observation:** Email ranked #1 in all three behaviour columns simultaneously:
- Engagement Rate: **76.7%** (highest)
- Avg. Engagement Time: **1:57** (highest)
- Views per Session: **6.65** (highest)

Then I checked the Sessions column to flag the volume contrast: **343 sessions** — the second lowest of all channels. The gap between quality (top of every column) and volume (near the bottom) is the core insight. No calculation needed — this is a visual scan of the table.

</details>

---

### 5. New Users Are Outpacing Returning Users — A Retention Risk
The Users vs. New Users time series shows new users consistently running close to total users throughout the month, meaning the site is heavily acquisition-dependent. With 73,691 new users out of 92,154 total, **roughly 80% of all users this month were first-time visitors**. For a merch shop, repeat purchase behaviour and brand loyalty are key revenue drivers — the current acquisition-heavy mix suggests a retention gap that will become expensive if ad costs rise.

<details>
<summary>📊 How I got to this insight</summary>

**Where I looked:** Two places — the Users vs. New Users time series chart, and the scorecard numbers at the top.

**Visual observation (time series):** The two lines (Total Users and New Users) run very close together for the entire 30-day period. A healthy retention mix would show a clear gap between the two lines, with Total Users meaningfully higher than New Users. Here, the gap is narrow, meaning very few sessions are coming from returning users.

**Calculation (scorecards):**
- New users: **73,691**
- Total users: **92,154**
- New user share: 73,691 ÷ 92,154 = **79.9%**

Nearly 8 in 10 users this month had never visited before. That's the retention problem in one number.

</details>

---

### 6. The Homepage Is a Funnel Leak
The homepage (`/`) drives 304,655 session starts — far more than any other page — but has only a **27.9% engagement rate**, by far the lowest of any tracked page. Meanwhile, product category pages like `/shop/clearance` (89.6%), `/shop/apparel/mens` (87.2%), and `/shop/new` (82.6%) perform dramatically better. Users who land directly on product pages are far more engaged. This suggests homepage content and CTAs need rethinking, and that paid campaigns should bypass the homepage and land users directly on high-intent product pages.

<details>
<summary>📊 How I got to this insight</summary>

**Where I looked:** Landing Page Performance table — Session Start column and Engagement Rate column.

**Observation 1 — volume:** Scanned the Session Start column. The homepage (`/`) has 304,655 session starts — more than 3× the next highest page (`/shop/new` at 87,643). It is by far the most common entry point.

**Observation 2 — engagement:** Scanned the Engagement Rate column for the same rows. The homepage sits at **27.9%**, while every product page listed is above 80%:

| Page | Engagement Rate |
|---|---|
| `/shop/clearance` | 89.6% |
| `/shop/apparel/mens` | 87.2% |
| `/shop/new` | 82.6% |
| `/shop/lifestyle/bags` | 83.9% |
| `/` (homepage) | **27.9%** |

The contrast is immediate just by scanning the column — no calculation needed. The homepage is receiving the most traffic and producing the least engagement. That combination defines a funnel leak.

</details>

---

## Findings & Recommendations

**Finding 1: The traffic mix is skewed toward low-engagement Direct traffic.**  
*Recommendation:* Investigate what is attributing to Direct (implement UTM tagging on all campaign links, especially newsletters and internal promotions). Improving attribution accuracy will likely reveal hidden high-performing channels and help allocate budget more intelligently.

**Finding 2: Paid Search delivers strong ROI per session but appears underscaled.**  
*Recommendation:* Increase Paid Search budget incrementally and monitor revenue-per-session as a primary efficiency metric, not just click volume. Test campaign expansion into longer-tail commercial keywords aligned with top-performing product categories (clearance, mens apparel).

**Finding 3: Email is a high-intent, underutilised channel.**  
*Recommendation:* Prioritise list growth and increase send cadence. Given the 1:57 average engagement time and 6.65 views per session, email users are clearly warmed up and ready to buy. A simple re-engagement or browse-abandonment flow targeting returning users could materially lift revenue without increasing ad spend.

**Finding 4: The homepage converts poorly as a landing page.**  
*Recommendation:* Redirect paid traffic to high-engagement product category pages (`/shop/new`, `/shop/clearance`). A/B test homepage layout to reduce bounce — in particular, add visible, direct-to-category CTAs above the fold.

**Finding 5: Retention is weak — the site runs on new user acquisition.**  
*Recommendation:* Implement a loyalty or repeat-purchase incentive (discount on second order, wishlist reminders). Track returning user rate as a KPI alongside new user growth. A balanced acquisition-to-retention ratio is healthier long-term, especially if ad costs increase.

---

## Tools & Techniques Used

| Tool | Purpose |
|---|---|
| **Looker Studio** | Dashboard design, visualisation, and publishing |
| **GA4 (Google Analytics 4)** | Source data — sessions, users, events, engagement metrics |
| **Cross-filtering** | All charts and tables are linked — clicking any element filters the full dashboard |
| **Conditional formatting** | Heatmap-style colouring in the Channel Performance table to surface outliers visually |
| **Scorecards with sparklines** | Period-over-period % change for instant trend context |
| **Dual time series** | Separate charts for user acquisition trends and conversion trends |
| **Segmented data table** | Column groups (Acquisition / Behavior / Conversions) mirror the marketing funnel structure |
| **Control filters** | Channel group, device category, and date range filters enable self-serve analysis |
