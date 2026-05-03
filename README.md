# GA4-Traffic-Source-Dashboard
Used Google Merch Shop Demo Data to build a dashboard on Looker Studio for a marketing or growth team that needs to quickly understand channel quality, identify where to invest or cut spend, and monitor whether conversion trends are healthy.

**Tools:** Looker Studio · Google Analytics 4 (GA4) · Google Merch Shop Demo Data  
**Live Dashboard:** [View on Looker Studio](https://datastudio.google.com/reporting/ea37a056-df62-44dd-a779-a45d0baa93c9)  
**Period analysed:** April 3 – May 2, 2026

---

## Project Objective & Motivation
The Google Merch Shop is growing fast: sessions increased by 42% and total users increased by 56% compared to the previous year.
There's one clear problem: engagement rate has dropped 39.8% and average engagement time has fallen too. 
In this project I analyze exactly this gap between traffic growth and engagement quality.

**The question I answer is not only "where is the traffic coming from?" but also "which channels are actually worth it?"**

---

## Business Questions (KPIs)
1. **Which channels drive the most traffic & which drive the most engaged users?** (Volume vs. quality)
2. **What is the revenue contribution of each channel, and which paid channels deliver the best ROI?** (Paid Search vs. organic benchmarks)
3. **Is new user acquisition growing faster than retained user engagement?** (Acquisition health over time)
4. **Which landing pages are the strongest entry points into the purchase funnel?** (Page-level conversion efficiency)
5. **How are overall conversions trending — and do traffic spikes translate into conversion spikes?** (Volume vs. intent alignment)

---

## Dashboard
<img width="2500" height="3645" alt="GA4_Traffic_Source_Dashboard" src="https://github.com/user-attachments/assets/b3cb559e-e5f8-4448-81ed-23324ef0c498" />


> 🔗 [click to open interactive dashboard](https://datastudio.google.com/reporting/ea37a056-df62-44dd-a779-a45d0baa93c9)

---

## Dashboard Design — What I Built & Why

### Controls & Filters
The dashboard opens with three interactive filters: **Session Default Channel Group**, **Device Category**, and a **Date Range picker**. With cross-filtering enabled, it makes the entire dashboard reactive. If you click e.g. "Paid Search" in the donut chart or filter by "Mobile" in the dropdown every single chart and table updates. This enables the dashboard to serve multiple use cases and analysis goals.

### Scorecards — Quick overview
Looking at the five scorecards at the top (Sessions, Total Users, Engagement Rate, Avg. Engagement Time, Conversions) you can quickly answer if the business is "healthy". I included a sparkline trend and a percentage change vs. the previous year. I included volume metrics (Sessions, Users) as well as quality metrics (Engagement Rate, Avg. Time) which showed me the core problem in this dataset. Sessions and users increased but they struggle with engagement.

### Donut Chart — Top Channels by Users
This chart enables a proportional comparison of channels. Clicking any slice cross-filters the entire dashboard to that channel only. Direct dominates at **44.3%** — nearly as large as the next two channels combined (Organic Search at 31.7% and Cross-network at 9.4%). This immediately tells where the majority of traffic comes from, while the interactive filter allows deeper channel-specific analysis.

### Time Series — Users vs. New Users; Conversions
The **Users vs. New Users** chart tracks acquisition health. Answers: Are we growing the base or re-engaging the same people? The **Conversions** chart tracks purchase intent independently.

### Channel Performance Table — Acquisition + Behavior + Conversions
This is the core analytical part of the dashboard. I structured it across three column groups — Acquisition (Sessions, Active Users, New Users), Behavior (Engagement Rate, Views per Session, Avg. Engagement Time), and Key Events/Conversions (Key Events, Purchase Revenue). The table mirrors the marketing funnel. You can see for each channel group, who got acquired, how they behave, and whether they convert.

### Landing Page Performance Table
This table answers which page the user landed on and how engaged they were.

---

## Business Insights — Answering the Questions

### 1. Volume ≠ Quality: Direct Traffic is dominating ... but engagement is low
Direct traffic accounts for **71,424 sessions (66% of all traffic)**, generating the most revenue in absolute terms ($95,630). But its engagement rate is only **22.4%** and average engagement time is just 36 seconds — the worst of any meaningful channel. This means the majority of sessions are low-intent: people landing and leaving quickly. Direct is the biggest channel by volume but the weakest by quality. The traffic surge (+42% sessions) is largely driven by Direct, which explains why overall engagement rate dropped by 39.8% even as total volume grew.

<details>
<summary> How I got to this insight</summary>

Looked at Channel Performance table — Sessions column and Engagement Rate column.

**Calculation 1 — traffic share:**
- Direct sessions ÷ Grand total sessions = 71,424 ÷ 108,097 = **66%**

**Calculation 2 — key events per session (quality check):**
- Direct: 39,131 key events ÷ 71,424 sessions = **0.55 key events per session**
- This means the average Direct session doesn't complete one tracked action

**Observation:** Scanning the Engagement Rate column row by row, Direct is 22.4% while every other meaningful channel is above 60%. That contrast is immediate and flags Direct as a low-quality traffic source despite its volume dominance.

</details>

---

### 2. Organic Search Is the Highest-Quality Scalable Channel
With 16,430 sessions, **68.9% engagement rate**, and $31,345 in revenue, Organic Search is the clearest channel for investment opportunity. It brings qualified users who actually explore the site (3.94 views/session, 1:00 avg engagement time). Crucially, Organic Search users generate more key events *per session* than any other high-volume channel. It means they don't just visit passively, but also act and fulfill key events. Growing SEO content and optimising for commercial keywords should be a priority.

<details>
<summary> How I got to this insight</summary>

I looked at the Channel Performance table —> Organic Search row, across all columns.

**Calculation 1 - key events per session:**
- Organic Search: 19,081 key events ÷ 16,430 sessions = **1.16 key events per session**
- Compare with Direct: 39,131 ÷ 71,424 = **0.55 key events per session**
- Organic Search users complete **2× more tracked actions per session** than Direct users

**Calculation 2 — revenue per session:**
- Organic Search: $31,345 ÷ 16,430 = **$1.91 per session**
- vs Direct: $95,630 ÷ 71,424 = **$1.34 per session**
- Organic Search earns more per session despite having no ad spend behind it

</details>

---

### 3. Paid Search Has the Best Revenue-Per-Session Ratio Among All Channels
Paid Search drives only 3,204 sessions but generates **$19,437 in revenue** — the highest revenue efficiency of any channel. Its engagement metrics are pretty solid too (61.9% engagement rate, 1:12 avg engagement time), confirming it is capturing high-intent buyers, not just casual browsers. 

--> Implication for the business: Think about if the current budget is too conservative. Paid search could scale a lot.

<details>
<summary> How I got to this insight</summary>

Looked at Channel Performance table — Paid Search row, Purchase Revenue and Sessions columns.

**Calculation — revenue per session across channels:**

| Channel | Sessions | Revenue | Revenue/Session |
|---|---|---|---|
| Paid Search | 3,204 | $19,437 | **$6.07** |
| Organic Search | 16,430 | $31,345 | $1.91 |
| Referral | 2,468 | $10,586 | $4.29 |
| Direct | 71,424 | $95,630 | $1.34 |
| Email | 321 | $1,868 | $5.82 |

Paid Search leads all channels in revenue per session at $6.07. Email is close at $5.82 but has 10× fewer sessions, making it much harder to scale. Paid Search is therefore the most actionable high-ROI lever.

</details>

---

### 4. Email Is the Highest-Intent Channel - But Almost Invisible
Email has only 321 sessions, but its metrics are very good: **77.6% engagement rate, 1:59 average engagement time, 6.74 views per session** —-> scores extremely high across all three behaviour metrics. Email users are the most engaged visitors which presents high potential. The issue is the volume. Reason could be that the email list or send frequency is underutilised.

<details>
<summary> How I got to this insight</summary>

Looked at Channel Performance table — Engagement Rate, Avg. Engagement Time, and Views per Session columns across all rows.

**Observation:** Email ranks extremely high across all three behaviour columns:
- Engagement Rate: **77.6%** (very high)
- Avg. Engagement Time: **1:59** (very high — only Organic Video exceeds it at 2:10, but with just 15 sessions)
- Views per Session: **6.74** (highest across all channels)

Then I checked the Sessions column: **321 sessions** — very low compared to all channels. There is a gap between quality and volume.

</details>

---

### 5. New Users Are Outpacing Returning Users — A Retention Risk
The Users vs. New Users time series shows new users are consistently close to total users throughout the month, meaning the site is very much dependent on new acquisitions. With 73,060 new users (see channel performance table) out of 91,369 total (see scorecard), **roughly 80% (73,060 ÷ 91,369 = 80.0%) of all users this month were first-time visitors**. For a merch shop, repeat purchase behaviour and brand loyalty are important as they present key revenue drivers. The retention problem needs to be addressed as acquisition will become expensive if e.g. ad costs rise.

---

### 6. The Homepage Is a Funnel Leak
Looking at the Landing Page Performance table, the homepage (`/`) drives 300,802 session starts — far more than any other page — but has only a **27.3% engagement rate**, which is pretty low. Meanwhile, product category pages like `/shop/clearance` (89.8%), `/shop/apparel/mens` (87.1%), and `/shop/new` (82.4%) perform dramatically better. Users who land directly on product pages are more engaged. This suggests a redesign of homepage content, and that paid campaigns should land users directly on product pages and not lead to the homepage first.

---

## Findings & Recommendations

**Finding 1: The traffic mix is skewed toward low-engagement Direct traffic.**  
*Recommendation:* Investigate what is attributing to Direct (implement UTM tagging on all campaign links, especially newsletters and internal promotions). Improving attribution accuracy will likely reveal hidden high-performing channels and help allocate budget more intelligently.

**Finding 2: Paid Search delivers strong ROI per session but appears underscaled.**  
*Recommendation:* Increase Paid Search budget incrementally and monitor revenue-per-session as a primary efficiency metric, not just click volume. Test campaign expansion into longer-tail commercial keywords aligned with top-performing product categories (clearance, mens apparel).

**Finding 3: Email is a high-intent, underutilised channel.**  
*Recommendation:* Prioritise list growth and increase send cadence. Given the 1:59 average engagement time and 6.74 views per session, email users are clearly warmed up and ready to buy. A simple re-engagement or browse-abandonment flow targeting returning users could materially lift revenue without increasing ad spend.

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
