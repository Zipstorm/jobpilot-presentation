# Hackathon Demo Presentation: Job Application Extension

**Date**: 2026-02-26
**Format**: ~5 minute presentation + live demo
**Audience**: SeekOut leadership & engineering

---

## Slide 0: Title

**JobPilot**

Kailash Yogeshwar & Akshay Gupta

---

## Slide 1: The Moat Has Shifted

**Key message**: Software moats are commoditizing. The moat is now users and networks.

- LLMs mean anyone can build features overnight — software alone is no longer defensible
- The moat is now *users and networks* — who has the people, the data, the engagement loop
- That's why LinkedIn is worth $26B to Microsoft — it's the network, not the software

---

## Slide 2: Helix Needs Prospects — What's the Hook?

**Key message**: The hardest side to bootstrap is always supply. We need a reason for job seekers to come to SeekOut.

- Helix is a 3-sided network: prospects, recruiters, hiring managers
- The hardest side to bootstrap is always the *supply side* — the prospects
- You need a reason for job seekers to come to SeekOut and create a profile
- What's a pain point so acute that millions of people will install a tool for it?

---

## Slide 3: The Pain — Applying to Jobs Today

**Key message**: The real time sink is custom questions, not name/email fields.

**Visual**: Screen recording / gif of someone copying a question into ChatGPT, typing a rough answer, getting a mediocre reply, pasting it back into the form field, then repeating for the next question.

- 15-30 minutes per application
- 5-8 custom questions per form
- Browser autofill handles name/email but can't touch open-ended questions
- Most candidates today copy questions into ChatGPT → get mediocre, generic answers → paste back
- This is what millions of people do *today*

---

## Slide 4: This Is a Validated Market

**Key message**: You don't need to guess whether people want this solved — they already do. Six Chrome extensions competing for the same use case.

| Extension | Chrome Users | Rating | Reviews |
|-----------|-------------|--------|---------|
| **Simplify Copilot** | 500,000 | 4.9 ★ | 3,500 |
| **Teal** | 200,000 | 4.9 ★ | 3,100 |
| **Careerflow** | 200,000 | 4.4 ★ | 283 |
| **JobFill (Autofill Smartly)** | 20,000 | 4.3 ★ | 113 |
| **LazyApply** | 20,000 | 3.0 ★ | 174 |

**Combined Chrome installs: ~940K users** across these 5 extensions.

**Market size**: AI recruitment tools market $1.78B (2024) → $7.12B by 2033 (17.4% CAGR). AI usage for resumes/cover letters more than doubled from Feb 2024 to Jan 2025.

**Bottom line**: Small teams, modest funding, nearly 1M Chrome extension users. The demand is overwhelming.

---

## Slide 5: Demo

**Live demo on a real Greenhouse job application page.**

Flow:
1. Open a real Greenhouse application (e.g., Anthropic, Discord)
2. Extension detects the page → floating nudge appears with question count
3. Click "Auto-fill Application"
4. Side panel opens — shows real-time streaming progress
5. Standard fields (name, email, phone) fill instantly
6. Custom questions fill one-by-one with AI-generated, role-specific answers
7. Each field highlights as it fills — the "magic" moment
8. Done in ~30 seconds

**Let the demo speak. Keep narration minimal.**

---

## Slide 6: Why We Can Do This Better

**Key message**: Two things competitors don't have.

### 1. LLM-Grade Tailoring (Not Keyword Matching)

Competitors store your profile and do keyword-level field matching — find "Python" in your resume, paste it into a skills field.

We use Claude to generate *role-specific, company-specific answers* to open-ended questions in real time — drawing on the full job description and your complete career history.

- Competitor answer to "Why do you want to work here?": Generic template with company name swapped in
- Our answer: References specific details from the job description, connects to relevant experience from the candidate's history, tailored to the company's mission

The quality gap is immediately visible.

### 2. Trackable Profile Link

We generate a tailored `seekout.ai/username` profile link and embed it in the application.

The candidate gets something no other tool offers:
- Was my application opened?
- Who viewed it?
- How long did they spend?

This is the Helix custom link concept applied to external applications. **No competitor does this.**

---

## Slide 7: How This Feeds Helix (The Flywheel)

**Key message**: This is a prospect acquisition engine disguised as a productivity tool.

```
Install extension → Create SeekOut.ai profile
        ↓
Apply to jobs (with trackable profile link)
        ↓
Candidate gets traction analytics (views, visitors)
        ↓
HMs/recruiters view beautiful profile → some sign up
        ↓
More profiles = more value for recruiters
        ↓
More jobs posted on Helix
        ↓
More reasons to use the extension
        ↓
    ← FLYWHEEL →
```

**Every application = a new node in the Helix network.**

- Extension user creates a SeekOut.ai profile to power the auto-fill
- Every application includes a trackable profile link
- Candidate gets traction analytics — was it viewed? by whom?
- HMs/recruiters who view the profile see a beautiful page — some sign up
- More profiles = more value for recruiters = more jobs = more reasons to use the extension

**Framing**: "This is an experiment to test whether this flywheel works. If it does, it's our prospect onramp for Helix."

---

## Slide 8: Vision (TBD)

- Phase 1 / Phase 2
- Phase 1 - Integrate with Helix, Auto-create tailored profile website, Build auto-fill for other ATS job pages 
- Phase 2 - Tailored Resumes
- Simple closing statement

---

## Appendix: Competitor Chrome Extensions

### Simplify Copilot — 500,000 Chrome users
- **Rating**: 4.9 stars, 3,500 reviews
- **Funding**: $4.35M (YC W21, Craft Ventures) · Valuation: $20M
- **Revenue**: ~$4.2M estimated · ~10 employees
- **What they do**: Autofill job applications, job tracker, AI resumes
- 1M+ job seekers globally, 100M+ applications filled

### Teal — 200,000 Chrome users
- **Rating**: 4.9 stars, 3,100 reviews · Chrome Web Store Favorite 2023
- **Funding**: $19M total (Series A, Jan 2025, CityLight Capital + Flybridge)
- **Revenue**: Freemium model, Teal+ at $9/wk or $29/mo or $79/3mo
- **What they do**: Job tracker, AI resume builder, bookmarks from 40+ job boards

### Careerflow — 200,000 Chrome users
- **Rating**: 4.4 stars, 283 reviews
- **What they do**: Job application tracker, ATS resume checker, autofill, LinkedIn optimization

### JobFill (Autofill Smartly) — 20,000 Chrome users
- **Rating**: 4.3 stars, 113 reviews
- **What they do**: Smart autofill for any form, custom rules, auto-capture, AI job description summarization, resume tailoring

### LazyApply — 20,000 Chrome users
- **Rating**: 3.0 stars, 174 reviews (poor)
- **Pricing**: $99-$999/year
- **Issues**: Users report LinkedIn accounts flagged, inaccurate submissions

### Market Data
- AI recruitment tools market: $1.78B (2024) → $7.12B by 2033 (17.4% CAGR)
- AI usage for resumes/cover letters more than doubled Feb 2024 → Jan 2025
- 80% of job seekers using AI tools report faster, more relevant matches
