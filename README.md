# Subspace.money — Product Teardown

**By Anurag Ugargol · Product Intern Assignment · 31 May 2026**

> *I'm an active Hubble user. Here are the 5 things that would make me switch to Subspace.*

This is a product teardown based on roughly five hours of real, hands-on usage of subspace.money (both incognito and logged in), a head-to-head gift card price comparison with Hubble on three brands, and a companion test of Vocallabs.ai. Every finding below is grounded in something I actually saw on screen — the supporting screenshots are saved in the `/screenshots` folder of this repository and referenced inline at each finding.

---
## Executive Summary

Subspace has built more genuine fintech infrastructure than any competitor in its folder — a stored-value wallet, recurring-payment auto-detection, native group payments, and a six-product range. But it markets itself as a discount app, leads with its weakest (commodity) product, and ships visible trust-breaking bugs in a category where trust is the entire game. Its single defensible product — group subscription sharing — is buried below the fold and gated by a missing trust layer that its direct competitor Hubble already solved.

My five sharpest findings, one per product pillar:

1. **GTM & ICPs** — The only product with network effects (Shared Subscriptions) is buried four sections below the fold, while the zero-moat commodity (gift cards) leads. The homepage tries to say eight things and ends up saying nothing.
2. **Competitor Analysis** — Hubble shows a "100% money-back" trust badge on every page; Subspace shows none. On price, Subspace and Hubble each win roughly half the brands — a tie, which a smaller player loses.
3. **Features / Services** — In one checkout flow I found a live untranslated developer string, a data mismatch between listing and checkout, a 5% fee at 2–5× the category norm, a monthly plan showing a renewal date one year out, QR-only payment, and four of six marketed products missing from the web entirely.
4. **UX** — The trust mechanism (host chat) exists and is correctly wired into the join flow, but opens to a psychologically empty window: no host greeting, no verification badge, no rating — exactly when the buyer needs reassurance most.
5. **Potential Collaborations** — Zero visible partnerships. The wallet and auto-detect IP that Hubble structurally cannot replicate sits locked inside Subspace's own app instead of being distributed through neobanks or sold as a B2B API.

The throughline: **Subspace has the technology; it is losing on trust, focus, and distribution.** None of the fixes require new core technology — they require sequencing, trust UX, and partnerships.

---
## Table of Contents

1. [Who I am](#who-i-am)
2. [Product Overview (7Ps)](#product-overview-7ps)
3. [SWOT](#swot)
4. [Ideal Customer Profile (Porter's Five Forces)](#ideal-customer-profile)
5. [Competition Analysis](#competition-analysis)
6. [Pillar 1 — GTM & ICPs](#pillar-1--gtm--icps)
7. [Pillar 2 — Competitor Analysis](#pillar-2--competitor-analysis)
8. [Pillar 3 — Features / Services](#pillar-3--features--services)
9. [Pillar 4 — UX](#pillar-4--ux)
10. [Pillar 5 — Potential Collaborations](#pillar-5--potential-collaborations)
11. [GTM Blueprint (STP)](#gtm-blueprint-stp)
12. [Prioritization (RICE)](#prioritization-rice)
13. [Vocallabs Appendix](#vocallabs-appendix)
14. [Sources](#sources)

---
## Who I am

- Electronics engineering background, transitioning into AI / Product. Marks card arrives end of this month, so I'm **available full-time and open to a PPO conversion** after the internship.
- Hands-on with AI agents and automation — personal projects live at [github.com/AnuragU03](https://github.com/AnuragU03).
- Real-world shipping experience: production AI agents, voice flows, payment integration, multi-agent orchestration — end-to-end as a solo builder.
- I chose Subspace over Vocallabs because I'm already the ICP: an active Hubble user and group-buyer. I can critique this product from inside the buyer's head, not from the outside as an analyst.

---
## Product Overview (7Ps)

The 7Ps lens forces a complete description of the business before any critique.

| P | Subspace |
| --- | --- |
| **Product** | Six product lines marketed: Subscription Sharing, Gift Cards, Rentals in 10 minutes, Bills Auto-detect, Group Savings, P2P Group Credit Card |
| **Price** | Free app · gift card discounts 1.5%–20% (varies sharply by brand) · 5% convenience fee on subscription shares · Netflix Premium at ₹163/device |
| **Place** | Web (subspace.money), Android, iOS (launched March 2026 — roughly 18 months after Android) |
| **Promotion** | Founder-led LinkedIn presence, referral codes, organic Reddit, no visible paid advertising |
| **People** | IIT Madras founders · ₹36.5 Cr ARR (FY25) · bootstrapped and profitable · ~11–50 person team · CEO transition to Anupam Sharma in March 2026 |
| **Process** | No-login browsing · WhatsApp OTP (failed in my test) · phone OTP (instant) · QR-only checkout · built-in wallet |
| **Physical Evidence** | Play Store self-claim: "India's No.1 Savings, Sharing and Rental App" |


*Screenshot in repo — the homepage is dense, dark, and motion-heavy: three rotating carousels, a scrolling deal ticker, and neon-purple gradients. It reads like an Indian news channel's "breaking news" screen rather than a clean fintech.*

![Figure 1 — Subspace homepage overview](ScreenShot/figure%201.png)
![Figure 2 — Homepage carousel and deal ticker](ScreenShot/figure%202.png)
![Figure 3 — Homepage neon-purple gradient layout](ScreenShot/figure%203.png)

**Takeaway:** Subspace is six products inside one app. That breadth is the source of both its retention potential and three of the five problems below.

---
## SWOT

This frames where Subspace sits today and identifies the competitive set — without yet passing judgement.

| &nbsp; | Internal | External |
| --- | --- | --- |
| **Positive** | **Strengths** — Bootstrapped and profitable (rare in consumer fintech) · six-product breadth as a retention hook · wallet infrastructure competitors lack · IIT-M founder pedigree · genuine network effects in sharing · wide monthly + yearly subscription range | **Opportunities** — India's subscription economy is expanding · a rent-vs-own shift in Tier 1/2 cities · the DPDP Act makes consent visibility a buying factor · a new CEO is a natural moment to refocus the product |
| **Negative** | **Weaknesses** — six products dilute focus · visible production bugs · no trust badges anywhere · 5% fee at 2–5× category norm · a cultural-design straddle that satisfies neither camp | **Threats** — **Hubble** (5L users, ₹10 Cr saved, B2B SDK pivot) · magicpin · Woohoo / GyFTR / Zingoy · CRED / Jupiter / Fi / Slice · and most critically, **Netflix and Spotify household-enforcement, which is a legal kill switch on Subspace's flagship product** |


**Takeaway:** The single largest external risk is not a competitor — it is Netflix's policy team. The flagship product is built on a foundation a third party can remove overnight.

---
## Ideal Customer Profile

Porter's Five Forces, applied to derive *who* Subspace should target rather than just describing rivalry.

| Force | Pressure | Implication for the ICP |
| --- | --- | --- |
| Threat of new entrants | High | Gift card resale has no moat — any fintech can add it. The ICP must value the *bundle*, not the gift card. |
| Bargaining power of buyers | High | The average user has 10+ deals apps installed; switching cost is zero. The sharing flywheel is the only real lock-in. |
| Bargaining power of suppliers | Medium-High | Brand discounts vary month to month, so Subspace's margin sits at the brand's mercy. |
| Threat of substitutes | High | Credit card cashback, magicpin, brand-direct loyalty, and Hubble all substitute easily. |
| Competitive rivalry | Very High | 15+ named Indian players compete for the same buyer's screen. |


**The ICP that survives this analysis:**

- **Primary** — Indian Gen-Z and young millennials (18–28), Tier 1/2 cities, group-native (already on Splitwise, already sharing Netflix with roommates, dining out 2–3× a week).
- **Secondary** — cost-conscious working professionals (28–40) with four or more active subscriptions who want *visibility and control*, not just a discount.
- **Not the ICP** — CRED's premium, status-driven demographic; and Tier 3/4 users with fewer than two subscriptions to manage.

**Takeaway:** Buyer power is the dominant force. The ICP is not "anyone who wants discounts" — it is specifically the group-native young user, because only the sharing flywheel can lock them in against a folder full of substitutes.

---
## Competition Analysis

| Player | Core wedge | Strength | Weakness vs Subspace |
| --- | --- | --- | --- |
| **Hubble** | Gift cards (5L users, 400+ brands) | "Hubble Assured" trust badge · B2B Rewards SDK · WhatsApp delivery | No subscription sharing · no auto-detect |
| **magicpin** | Offline dine-in | Huge offline merchant network | No subscription management |
| **Woohoo / GyFTR** | Gift card marketplaces | Large brand catalogue | Pure commodity, no community |
| **CRED** | Premium fintech rewards | Brand and UX leadership | Premium-only · no sharing |
| **Splitwise** | Bill splitting | Single-purpose dominance | No payments, no subscriptions |
| **Subspace** | **Bundle: cards + sharing + rentals** | **The only player offering all three** | But which one is the wedge? |


**Head-to-head gift card price comparison — my own data, same brands, same day:**

| Brand | Card value | Subspace | Hubble | Winner |
| --- | --- | --- | --- | --- |
| Amazon | ₹500 | ₹493 (1.5% off) | ₹490 (2% off) | Hubble |
| Pizza Hut | ₹500 | ₹448 (10.5% off) | ₹465 (~7% off) | Subspace |
| Domino's | ₹500 | ₹401 (19.85% off) | ~17% off | Subspace |


&nbsp;

![Figure 23 — Subspace Domino's gift card page (19.85% off)](ScreenShot/figure%2023.png)
![Figure 24 — Hubble Amazon gift card page (2% off, Hubble wins)](ScreenShot/figure%2024.png)
![Figure 25 — Subspace Pizza Hut gift card page (10.5% off, Subspace wins)](ScreenShot/figure%2025.png)

**Takeaway:** Subspace wins QSR/food, Hubble wins big e-commerce. A tie on price is a loss for the smaller player, because Hubble also carries scale and a visible trust badge that Subspace lacks.

---
## Pillar 1 — GTM & ICPs
### The moat is buried below the commodity

**(a) Observed** The homepage opens with three auto-rotating hero carousels, a scrolling deal ticker, and neon-purple gradients. Gift cards can be browsed without logging in — good for discovery, but it means Subspace cannot retarget a visitor who leaves. When I tried to sign up, the **WhatsApp OTP never arrived after a 20-minute wait, with no fallback link offered**; the phone OTP, by contrast, arrived in under a second. Most importantly, **Shared Subscriptions — the only product with genuine network effects — sits four sections below the fold.** I discovered it by accident, the same way AAA gamers once stumbled onto console account-sharing. I also spotted a **"Subscape 60% OFF" typo in Subspace's own deal ticker** — the company advertising itself, misspelled.

*Screenshots in repo: the Subspace homepage, and the Shared Subscriptions list (real supply exists — Netflix, Prime, JioHotstar with dozens of active groups — but it is hidden far down the page).*

![Figure 4 — Subspace homepage (first view)](ScreenShot/figure%204.png)
![Figure 5 — Shared Subscriptions list buried below the fold](ScreenShot/figure%205.png)
![Figure 6 — "Subscape" typo in deal ticker](ScreenShot/figure%206.png)

**(b) Problem** There is no single wedge. Hubble's homepage says one thing; Subspace's says eight, and buyers remember none of them. The strongest, most defensible product is invisible while the zero-moat commodity leads. And the funnel leaks at both ends — no-login browsing means no retargeting, while the broken OTP means signups fail at the last step.

**(c) Ship instead**

- Reposition the homepage hero around Shared Subscriptions: *"India's group subscription app. Share Netflix from ₹163. 100+ subscriptions, split with friends."*
- Tell the console account-sharing analogy publicly — Gen-Z understands it instantly.
- Fix the OTP funnel: add a "Didn't get it? Try phone instead →" fallback, and add Google Auth as a third option.
- Fix the "Subscape" typo — a five-minute change that is currently a daily credibility leak.
- Add a "Save for later" soft-signup pill on gift cards to capture lukewarm intent without a hard signup wall.

> **Tradeoff:** Demoting gift cards reduces short-term revenue visibility, but Hubble, Woohoo, and Zingoy have already won that commodity race. Sharing is uncontested — that is where the front door should point.

---
## Pillar 2 — Competitor Analysis
### Hubble has a badge. Subspace doesn't. That's the whole story.

**(a) Observed** The price war is genuinely split — Hubble wins Amazon, Subspace wins Pizza Hut and Domino's. But the decisive difference is trust signalling. **Hubble shows a "100% money-back guaranteed" badge on every gift card page; Subspace shows no trust badge anywhere.** Hubble's homepage also leads with "5L+ happy users · Saved ₹10 Cr · Safe & secure," none of which Subspace surfaces. On top of that, Subspace ships visible bugs a buyer notices in seconds: the Pizza Hut page lists the same ₹100 card twice, and its ₹250 card carries a *smaller* discount (7.85%) than its ₹100 and ₹500 cards (10.5%) — a backwards incentive. When I looked at Shared Subscriptions, my honest reaction as a buyer was: *I'd love to cut my Netflix bill this way, but there's no way to know if the host is trustworthy. I'd commit instantly if Subspace offered Hubble-style assurance.*

*Screenshots in repo: the Hubble vs Subspace Amazon pages (Hubble's money-back badge vs Subspace's none), and the duplicate Pizza Hut listing.*

![Figure 7 — Hubble Amazon gift card page with money-back badge](ScreenShot/figure%207.png)
![Figure 8 — Subspace Amazon gift card page (no trust badge)](ScreenShot/figure%208.png)
![Figure 9 — Duplicate Pizza Hut listing on Subspace](ScreenShot/figure%209.png)

**(b) Problem** Subspace cannot win gift cards on price alone — a tie against a larger, more-trusted competitor is a loss. Hubble's badge is precisely why its organic Reddit reviews say things like "₹75k transaction went through smoothly"; Subspace has no comparable trust artifact to point to. And the category-killer product, Shared Subscriptions, is gated by the *same* trust gap Hubble already closed for gift cards. The visible bugs only deepen the trust deficit in a category where money changes hands.

**(c) Ship instead**

- Ship **"Subspace Verified Host"** within 30 days, in three tiers: *Verified* (KYC plus five clean shares), *Subspace Assured* (escrow plus refund guarantee, funded by a ~1% fee), and a *Host Reputation Score* (Airbnb-style).
- Add a trust counter above the fold: *"₹X Cr saved · Y lakh users · Z active groups."*
- Fix the duplicate listing and the regressive discount tier — both are one-day backend fixes.
- Stop chasing Hubble on Amazon; double down where Subspace already wins — QSR, regional brands, and FlexiPay variable amounts.
- Own the comparison publicly: *"Hubble is for one-off gift cards. Subspace is for everything recurring."*

> **Tradeoff:** Trust infrastructure costs 1–2% margin on share transactions. Subspace is bootstrapped and profitable, so it can afford this — and the unlock is 5–10× volume on the one category Hubble structurally cannot enter.

---
## Pillar 3 — Features / Services
### Seven bugs and one dark pattern in a single checkout flow

**(a) Observed** Walking one Netflix-group checkout end to end surfaced an unusual concentration of issues:

1. An **untranslated developer string,** `quickPayments.noOptions`**, rendered live** in the home page's Quick Payments section.
2. A **data mismatch** — the same Netflix group showed "Slots: 2" on the listing page but "0/4 members" at checkout.
3. A **5% convenience fee** (₹163 + ₹8.15 = ₹171.15). It is disclosed, which is good, but the rate is 2–5× the category norm (UPI is 0%, Hubble charges 0% on gift cards), and the label "convenience fee" is vague.
4. A **monthly plan showing a "Next payment: May 30, 2027" date** — a full year out, implying either an undisclosed annual lock-in or a date bug.
5. **QR-only checkout** — no UPI Intent, no card, no netbanking. UPI Intent converts roughly twice as well on desktop.
6. **No counterparty-risk disclosure** — Netflix's Paid Sharing policy and Spotify's household rules mean the flagship product rests on an eroding legal foundation, yet the buyer is never warned.
7. **Four of six marketed products (Rentals, Bills Auto-detect, Group Savings, P2P Card) are absent from the web entirely** — the pitch does not match the shipped product.

To be fair, there is a real strength here too: the subscription range is wide and offers both monthly and yearly tiers across YouTube Premium, Apple One, ChatGPT Plus, Spotify Duo, Microsoft 365, and Coursera — genuine depth inside the one product Subspace ships fully.

![Figure 26 — Subspace subscription catalogue (monthly + yearly tiers)](ScreenShot/figure%2026.png)

*Screenshots in repo: the Netflix checkout (the "May 30 2027" date and the contradictory slot count), the untranslated `quickPayments.noOptions` string on the home page, and the 5% fee price breakdown.*

![Figure 10 — Netflix checkout showing "May 30 2027" renewal date](ScreenShot/figure%2010.png)
![Figure 11 — Slot count mismatch: listing shows "2" vs checkout "0/4"](ScreenShot/figure%2011.png)
![Figure 12 — Untranslated quickPayments.noOptions string on homepage](ScreenShot/figure%2012.png)
![Figure 13 — 5% convenience fee price breakdown](ScreenShot/figure%2013.png)

**(b) Problem** A live developer string in a money app signals that no one is watching the shop — fatal for trust. The slots mismatch makes users tell friends "Subspace lies about how full groups are." A 5% fee on a product whose entire pitch is *saving money* feels punitive. The "May 30 2027" copy, shown without explanation, is the kind of dark pattern Indian regulators have begun fining. QR-only checkout leaves an estimated 15–25% of conversion on the table. And Netflix enforcement is not hypothetical — Netflix added roughly 7 million paying users in Q4 2025 specifically by ending password sharing; India is a logical next market.

**(c) Ship instead**

- **This week:** fix `quickPayments.noOptions` and add a CI check that fails the build on any unrendered `xxx.yyy` key; reconcile the slot count between the listing and checkout APIs; standardize the slot label everywhere.
- **This sprint:** rename "Convenience Fee" to "Subspace Service Fee," reduce it to 2–3% or justify it ("covers the refund guarantee"), and reframe the math as *"You save ₹486. Fee ₹8. Net savings ₹478 — 73% off."* Fix the "May 30 2027" copy to state the renewal terms plainly.
- **Next sprint:** add UPI Intent as the primary CTA, with QR as fallback and cards/netbanking as a third tier.
- **This quarter:** disclose counterparty risk in-product and pair it with Subspace Assured; reposition the feature as "Group Buy" rather than "Account Sharing" for legal cover.
- **Next quarter:** ship Bills Auto-detect on web, or remove the four missing products from the homepage until they exist there.

> **Tradeoff:** Showing fees and risks explicitly lowers conversion in the short term, but earns long-term trust and regulatory safety — a trade a profitable company is well positioned to make.

---
## Pillar 4 — UX
### The trust feature exists. It just doesn't earn trust.

**(a) Observed** The address geolocation prompt asks for consent correctly — but the address then persists on every page, including ones where it is irrelevant. Hindi mode is cosmetic: section headers translate, but category labels stay in English. Encouragingly, the **host chat is correctly wired into the join flow** — there is a chat icon next to "Join Group" for every host. But the chat itself is **psychologically empty**: it opens to a blank window showing a stranger's name and a default avatar, with no host greeting, no verification badge, and — critically — none of the 5.0 rating that appeared on the listing page. The trust signal vanishes exactly when the buyer needs it most. Host cards also display cryptic, unlabelled data ("Hindi 30% · Bengali 0% · Tamil 70%"), and there are no marketplace primitives at all — no host profile page, no review text, no dispute history.

![Figure 27 — Address persisting on a non-delivery page](ScreenShot/figure%2027.png)
![Figure 28 — Host card with cryptic unlabelled language data](ScreenShot/figure%2028.png)

*Screenshots in repo: the chat icon on the listing (chat is wired into the flow), the empty host chat (no trust signals), and the Hindi mode page.*

![Figure 14 — Chat icon on group listing (correctly wired)](ScreenShot/figure%2014.png)
![Figure 15 — Empty host chat window with no trust signals](ScreenShot/figure%2015.png)
![Figure 16 — Hindi mode with untranslated category labels](ScreenShot/figure%2016.png)

**(b) Problem** Address persistence on irrelevant pages reads as surveillance and erodes trust. Cosmetic Hindi is a false accessibility claim that will churn the very Tier 2/3 users Subspace markets to. Above all, **the chat is the trust mechanism and it is empty** — a buyer who wants to verify a host opens a blank window, doesn't know what to say, and leaves. The infrastructure exists but cannot do its job. And without any reputation surface, a good host's track record can never compound over time.

**(c) Ship instead**

- Show the address only on Rentals pages, where delivery actually occurs.
- Either deep-localize categories fully or remove the Hindi toggle — half-translation is worse than none.
- **Make the chat trustworthy (highest-leverage UX fix):** add a host auto-greeting (*"Hi, I'm Arani. 12 groups hosted, 0 disputes. Ask me anything."*), a chat-header trust block (photo, verified tick, rating, typical reply time), and tappable suggested questions. Add a **"Verified by Subspace" pill** that simultaneously closes the trust-badge gap from Pillar 2.
- Relabel the language data meaningfully, or remove it.
- Pick a cultural lane — A/B test the fintech-clean direction against the Indian-funky one for four weeks and let data decide.
- Build Airbnb-style host profile pages: bio, badge, past shares, rating, reviews, and current active groups.

> **Tradeoff:** Templated greetings and verification UI are roughly 4–6 weeks of work, but this is the multiplier that makes every other fix in the report actually convert.

---
## Pillar 5 — Potential Collaborations
### Distribution beats discounts. Subspace has zero distribution.

**(a) Observed** There are **no visible partnerships anywhere** on Subspace's web surface — no payment-gateway logo, no bank logos, no media credibility badges, no co-marketing. Yet Subspace has built real fintech infrastructure: a stored-value wallet with QR top-up, recurring-payment auto-detection, multi-product breadth, and native group payments. **None of it is exposed as a B2B or partnership API** — every primitive is locked inside the consumer app. By contrast, Hubble — a company of similar founder vintage — has already pivoted to a B2B "Rewards-as-a-Service" SDK that any consumer app can embed. My own admission captures the opportunity: *I would trust Subspace's Shared Subscriptions if Jupiter, Fi, Slice, or Razorpay endorsed it inside their app — even knowing the OTT household rules make sharing risky.* Brand-channel trust can override even known regulatory risk.

![Figure 29 — Subspace homepage with zero partnership or credibility logos](ScreenShot/figure%2029.png)
![Figure 30 — Hubble B2B Rewards SDK page (the benchmark)](ScreenShot/figure%2030.png)

*Screenshot in repo: the Wallet page — the wallet infrastructure Hubble structurally lacks, buried in checkout and unexposed as a B2B asset.*

![Figure 17 — Subspace Wallet page](ScreenShot/figure%2017.png)
![Figure 18 — Wallet QR top-up flow](ScreenShot/figure%2018.png)

**(b) Problem** Direct fintech customer acquisition in India runs ₹100–400 per install with 60–70% drop-off before the first transaction; at Subspace's ARPU, the unit economics break without partnership distribution. The wallet and auto-detect IP — Subspace's most defensible assets — generate no value while locked inside one app. Hubble is already monetizing the same buyer through *other* apps, while Subspace pays to fight Hubble head-on in the consumer funnel. And because the trust gap is bridgeable by brand transfer, embedded distribution is actually *faster* than fixing trust UX alone.

**(c) Ship instead**

- **Tier 1 (next 90 days):** embed Subspace as a tab inside one Indian neobank (Jupiter, Fi, Slice, or Jar) on a revenue-share basis — CAC drops to zero and the bank's trust transfers. Co-brand sharing as "Negotiated Group Plans" for legal cover.
- **Tier 2 (next 6 months):** launch a Subscription Manager API as a B2B product, sold to neobanks, HR/payroll platforms, and D2C brands — a direct counter to Hubble's SDK.
- **Tier 3 (12 months):** co-issue the P2P Credit Card with a bank (RBL, Bank of Baroda, IndusInd) rather than going solo.
- **This quarter:** add credibility badges to the homepage — "As seen on Inc42 / YourStory" plus "5L+ users · 4 years bootstrapped and profitable."

> **Tradeoff:** Partnerships are slow and give up margin through revenue share, but at the pre-Series-A stage, distribution velocity matters more than margin per transaction. The Subspace that wins is the one in the most apps, not the one with the deepest single discount.

---
## GTM Blueprint (STP)

**Segmentation → Targeting → Positioning**

- **Segment** the market by subscription count, group-native behaviour, and discount sensitivity.
- **Target** a beachhead of Indian Gen-Z group-native users with three or more subscriptions, Tier 1/2, ages 18–28.
- **Position** clearly: *"India's group savings app — share Netflix, rent gadgets, and buy gift cards together. Save 50–80%."*

| &nbsp; | Launch (90 days) | Support (continuous) | Sell (6 months) |
| --- | --- | --- | --- |
| **How** | College ambassador program, creator partnerships, Reddit AMAs by the CEO | WhatsApp support plus in-app chat; capture NPS every payment cycle | Self-serve for consumers; inside sales for neobank and D2C B2B deals |
| **Where** | Play Store ASO, iOS launch comms, Indian fintech Twitter | A public roadmap that shows users they're heard | Embed in neobank tabs; co-market with banks |
| **Feedback loop** | One weekly metric: of group invitees, how many actually paid? | A Customer Advisory Board of the top 100 hosts | Track partnership CAC against direct CAC every month |


---
## Prioritization (RICE)

| Rank | Ship | Impact | Effort |
| --- | --- | --- | --- |
| 1 | Fix `quickPayments.noOptions` + add i18n CI check | Critical | < 1 day |
| 2 | Reconcile the slots data mismatch | High | 2 days |
| 3 | WhatsApp OTP fallback + Google Auth | High | 1–2 days |
| 4 | Rename the fee + reframe the savings math | Medium | 3 days |
| 5 | Make the host chat psychologically trustworthy | Very High | 4–6 weeks |
| 6 | Reposition the homepage around sharing | Very High | 2–3 weeks |
| 7 | Ship "Subspace Verified Host" + Assured tiers | Very High | 6–8 weeks |
| 8 | Add UPI Intent at checkout | High | 1 week |
| 9 | Embed in one Indian neobank | Massive | 3–6 months |
| 10 | Productize the Subscription Manager API | High | 4–6 months |


**Sequencing logic:** trust bugs first (cheapest and deadliest), then trust UX (highest leverage), then distribution (slowest but most compounding).

---
## Vocallabs Appendix

*I tested both companies. I chose Subspace because it gave deeper findings — but Vocallabs' core product is genuinely impressive, and the honest version of this report shows both sides.*

**What works**

- **The homepage agent demo is excellent.** I tested it directly: the AI agent fluently pitched the product set and answered specifics on demand, clearly grounded in Vocallabs' own knowledge base. It is better than 80% of the voice demos I've tried, and I've shipped voice agents in production myself.
- **The VocalFlow open-source SDK** (`Vocallabsai/vocalflow`, Swift, on-device via CoreML) is positioned as "the first open-source alternative to Vapi, Retell, and Bland." That is a real community and moat candidate most VC-backed competitors don't have.
- **Founder pedigree and build velocity** — Joey Dash (IIT Madras), full-time on Vocallabs, shipping publicly at a fast clip.

*Screenshot in repo: the VocalFlow GitHub repository.*

![Figure 19 — VocalFlow GitHub repository](ScreenShot/figure%2019.png)
![Figure 20 — Vocallabs homepage agent demo](ScreenShot/figure%2020.png)

**What blocks me from buying**

- **No Google Auth and no self-serve sandbox** — onboarding requires a "Contact us for demo" form, where Vapi, Bolna, and Retell all hand out free credits and OAuth in under two minutes. I raised an access request on Day 1 and received no response by the submission day.
- **The verify-email link is broken** — the email sends `/auth/verify-email/<id>`, a relative path with no domain prefix, so it isn't clickable from any email client. The first interaction with the brand is effectively a 404.
- **The UI shows vibe-coded fingerprints** — a purple gradient and a lightning-bolt emoji baked into the "GET STARTED · 2 mins" button read as templated AI-codegen polish rather than deliberate brand design.

*Screenshots in repo: the Vocallabs "GET STARTED" button, and the broken verify-email link.*

![Figure 21 — Vocallabs "GET STARTED" button with vibe-coded styling](ScreenShot/figure%2021.png)
![Figure 22 — Broken verify-email link (relative path with no domain)](ScreenShot/figure%2022.png)

> **The disconnect:** the technology is real, but the funnel is broken. Vocallabs should fix the front door before scaling marketing — every Day-1 access request that goes unanswered is a Bolna customer.

---
## Sources

- Personal hands-on usage: subspace.money (web) and Hubble (Android)
- Play Store listings: Subspace, Hubble, Vocallabs, Vocalassist
- Reddit: r/indianstartups and r/CreditCardsIndia (Hubble safety thread, Subspace OTP thread)
- Inc42 and Business Upturn (March 2026 CEO transition coverage)
- Hubble: myhubble.money and its B2B Rewards SDK page
- Vocallabs: vocallabs.ai and github.com/Vocallabsai/vocalflow
- Regulatory references: Netflix Paid Sharing policy, TRAI TCCCPR 2018, DPDP Act 2023

---

---

*Anurag Ugargol · [github.com/AnuragU03](https://github.com/AnuragU03) · Available full-time, open to PPO conversion*
