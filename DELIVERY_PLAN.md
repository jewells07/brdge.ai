# Delivery plan: 6 weeks to both stores

Two people: **1 React Native (Expo)** and **1 Python (FastAPI + Postgres)**. Goal: submit to the App Store and Google Play at the end of week 6.

We ship a **smaller** product on purpose. Community can wait. Missing the store date cannot.

## What we ship

- Accounts (sign up, sign in, delete account).
- Project planner with a fast swatch (placeholder + tint + cache).
- Yarn inventory (personal stash tied to a project).
- AI assistant: Assignment A’s three tools only. No invented yarn amounts.
- 5–8 static learning guides the founder writes.
- Store listing, privacy policy, support email, crash reporting.

## What we cut

Community feed, follows, likes, comments, moderation. Social sharing. In-app purchases. Pattern marketplace. Push campaigns. iPad-only layouts. Live Ravelry search.

Community is its own product. Starting it in this window means we miss review.

## Week by week

**Week 1 — skeleton**  
Backend: login, users, empty `projects` and stash tables.  
Frontend: app shell, login, tabs (Planner / Stash / Guides / Account).  
Founder: Apple and Google developer accounts, app name, logo.

**Week 2 — data**  
Backend: create/edit projects and stash; yarn/needle/gauge APIs (no chat yet).  
Frontend: project form and stash list.  
Founder: 8 guide outlines.

**Week 3 — swatch + assistant API**  
Backend: Pillow + cache + tint; optional HQ image behind a flag; chat endpoint using A’s tools.  
Frontend: colour picker that updates instantly; chat screen stub.  
Founder: 8–12 palette hexes. OpenAI billing on.

**Week 4 — the product**  
Backend: guides as files or a small table; rate limits.  
Frontend: working chat, guide reader, one full path: new user → project → stash → swatch → one calculation.  
Both: crash reporting.  
Founder: screenshot text, a support inbox someone actually reads.

**Week 5 — store rules**  
Privacy policy URL, account deletion, Sign in with Apple, Android data-safety form.  
Frontend: TestFlight and internal Play track.  
Backend: production deploy.  
Feature freeze except review blockers.

**Week 6 — submit**  
Founder + a few knitters try it. Drop anything still broken (HQ images first, then chat polish, then a guide). Submit by Wednesday so we have days if the binary is rejected.

## Who does what

- **Backend:** database, login, calculators, assistant tools, swatch pipeline.
- **Frontend:** every screen, fast swatch UI, TestFlight / Play upload.
- **Shared:** API agreement in week 1; full path in week 4; review replies in weeks 5–6.

## Dependencies

- Apple + Google accounts (founder, week 1 — this can take days).
- OpenAI project and a spend cap (week 3).
- Privacy policy and terms (start in week 1, not week 5).
- Palettes and guide drafts (founder, weeks 2–3).
- Ravelry is **not** needed for MVP.

## Top risks

1. **Store review delay** — Sign in with Apple, delete account, privacy. Week 5 is only this work.
2. **Slow / expensive images** — colour is tint-only; HQ off by default; spend cap.
3. **Assistant inventing numbers** — ship A’s tools unchanged; refuse if data is missing.
4. **Two people, native modules** — stay on Expo; no push or widgets in v1.
5. **Guides late** — ship with 5 articles; do not block the binary on copy.

## What the founder must provide

**Week 1:** store accounts, name, icon, 8–12 colours, support email, someone who answers App Review the same day.

**Week 2:** privacy/terms draft, 8 guide drafts, confirm no in-app purchases in v1.

**Week 4:** screenshot headlines, age rating answers.

If content is late, we still submit a thinner app (calculators, stash, placeholder swatches, fewer guides). We do not add a community feed to fill the gap.
