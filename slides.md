# Hackathon Demo Presentation: Job Application Extension

**Date**: 2026-02-26
**Format**: ~5 minute presentation + live demo
**By**: Akshay Gupta & Kailash Yogeshwar
**Audience**: SeekOut leadership & engineering


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

**Key message**: You don't need to guess whether people want this solved — they already do.

| | Simplify | Jobright | Teal |
|--|----------|----------|------|
| **Users** | 1M+ job seekers, 400K Chrome installs | 520K+ users | 85K+ users |
| **Growth** | 100M+ applications filled | 30x YoY | Series A (Jan 2025) |
| **Funding** | $4.35M (YC W21, Craft Ventures) | $3.2M (backed by Indeed's venture arm) | $19M total |
| **Revenue** | ~$4.2M estimated | Profitable | Freemium, $9/wk premium |
| **Team** | ~10 employees | Small team | Small team |

**Also in the space**: LazyApply (~50K downloads), Sonara (shut down, acquired by BOLD)

**Market size**: AI recruitment tools market $1.78B (2024) → $7.12B by 2033 (17.4% CAGR). AI usage for resumes/cover letters more than doubled from Feb 2024 to Jan 2025.

**Bottom line**: Small teams, modest funding, already millions of users and real revenue. The demand is overwhelming.

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

## Appendix: Competitor Deep Dive

### Simplify Copilot
- **Users**: 400K+ Chrome users, 1M+ job seekers globally, 100M+ applications
- **Funding**: $4.35M across 3 seed rounds (Craft Ventures, Y Combinator W21)
- **Revenue**: ~$4.2M estimated
- **Valuation**: $20M (as of Sept 2022)
- **Rating**: 4.86 stars, ~2,800 reviews
- **Team**: ~10 employees
- **What they do**: Autofill job applications, job tracker, AI resumes

### Jobright
- **Users**: 520K+ professionals, 30x YoY growth
- **Funding**: $3.2M (June 2025, led by Translink Capital, backed by Indeed)
- **Revenue**: Profitable
- **What they do**: AI career agent that auto-finds, customizes, and submits applications
- **Claim**: Cuts job search time by 80%, doubles interview rates

### Teal
- **Users**: 85K+ job seekers
- **Funding**: $19M total (Series A, Jan 2025, CityLight Capital + Flybridge)
- **Revenue**: Freemium model, Teal+ at $9/wk or $29/mo or $79/3mo
- **What they do**: AI resume builder, job tracker, interview coach, Chrome extension

### LazyApply
- **Users**: ~50K downloads
- **Pricing**: $99-$999/year
- **Rating**: 1.9-2.5 stars on Trustpilot (poor)
- **Issues**: Users report LinkedIn accounts flagged, inaccurate submissions

### Sonara (Defunct)
- **Peak traffic**: 290K monthly visits
- **Status**: Shut down Feb 2024, acquired by BOLD (parent of LiveCareer, Zety)
- **Pricing was**: $20-$80/month

### Market Data
- AI recruitment tools market: $1.78B (2024) → $7.12B by 2033 (17.4% CAGR)
- AI usage for resumes/cover letters more than doubled Feb 2024 → Jan 2025
- 80% of job seekers using AI tools report faster, more relevant matches
