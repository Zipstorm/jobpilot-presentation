---
theme: default
title: "Helix Metrics: How We Measure and Grow a Network"
info: |
  Helix analytics framework — light formulas version.
  Includes key formulas: Helix Size, K = i x c, throughput = f x K.
---

# Helix Metrics

## How We Measure and Grow a Network

<!-- Speaker note: This version includes key formulas for Helix Size, K-factor, and throughput. Good for product and analytics audiences. -->

---

# Helix is a network, not a feature

Traditional recruiting tools are databases — you put candidates in, you search them, you pull them out.

Helix is different. Every user, every job, every expression of interest creates a **connection**. The value isn't in any single record — it's in the **structure** of connections between them.

The product question isn't "what features do we build?" It's **"how do we grow and strengthen the network?"**

---

# The network has four building blocks

![Helix Network Schema Graph](../../context/products/helix/network-schema-graph.png)

**User** — the actor. Can play any role depending on context.

**Job** — the connecting node. Every interaction flows through a job.

**Expression of Interest (EOI)** — the bridge between prospects and hiring teams.

**Custom Link** — the prospect's viral unit. A shareable profile link used in external applications.

---

# Personas live on edges, not on users

A single user can be a **hiring manager** on one job and a **prospect** on another.

The persona isn't an attribute of the person — it's determined by **which edge they're participating in**.

| Persona | Determined by |
|---------|---------------|
| Hiring Manager | Designated decision-maker on a job |
| Team (Recruiter / Member) | Collaborates on a job they didn't create as HM |
| Prospect | Expressed interest in a job via an EOI |

This means the same person can exist on both sides of the network simultaneously.

---

# Act 2: How Do We Measure It?

---

# Top-line metric: Helix Size

Helix Size measures the total weight of the network — users weighted by their connections to jobs.

$$\text{Helix Size} = (U_h \times T) + (U_p \times EOI)$$

| Symbol | Meaning |
|--------|---------|
| $U_h$ | Hiring-side users (at least one team collaboration edge) |
| $T$ | Total team edges (collaborates_on connections) |
| $U_p$ | Prospect-side users |
| $EOI$ | Total expressions of interest |

**Left term:** hiring-side users weighted by team connections. **Right term:** prospects weighted by interest expressions.

Helix Size goes up when we add users, add jobs, or create more connections.

---

# Network Health: three independent gauges

No composite score. Three metrics, each measuring a different structural property:

**Hiring-Side Liquidity**

$$\text{EOIs per Job} = \frac{EOI}{J}$$

Are jobs getting enough prospect interest? Too low and hiring managers churn.

**Prospect Activation**

$$\text{CLs per Prospect} = \frac{CL}{U_p}$$

Are prospects using custom links? Each link seeds Loop 5 (Custom Link Virality).

**Bridging**

$$\text{Bridging} = \frac{D}{U}$$

Fraction of users on both sides. $D$ = dual-persona users, $U$ = all users.

---

# The metric hierarchy

```mermaid
graph TD
    HS["Helix Size = (Uh x T) + (Up x EOI)"]
    HS --> HL["Hiring-Side Liquidity: EOIs per Job"]
    HS --> PA["Prospect Activation: CLs per Prospect"]
    HS --> BR["Bridging: D / U"]
    HL --> L1T["Loop 1: Job Sharing (f x K)"]
    HL --> L2T["Loop 2: Team Invite (f x K)"]
    PA --> L5T["Loop 5: Custom Link (f x K)"]
    PA --> L3T["Loop 3: Prospect Referral (f x K)"]
    BR --> L4T["Loop 4: Cross-Persona Bridge Rate"]
    L1T --> L1F["Job Sharing Funnel"]
    L2T --> L2F["Team Invite Funnel"]
    L3T --> L3F["Prospect Referral Funnel"]
    L4T --> L4F["Bridge Conversion Funnel"]
    L5T --> L5F["Custom Link Funnel"]
    L1F --> EV["Trackable Input Events"]
    L2F --> EV
    L3F --> EV
    L4F --> EV
    L5F --> EV
```

Each layer decomposes into the one below. Every trackable event rolls up to Helix Size.

---

# Act 3: How Does It Grow?

---

# Growth = completing viral loops

The network grows through **viral loops** — closed paths where each completion adds new nodes and edges.

Each loop has three key numbers:

$$K = i \times c$$

| Symbol | Meaning |
|--------|---------|
| $K$ | K-factor: new users generated per trigger event |
| $i$ | Invitations: people reached per trigger event |
| $c$ | Conversion: fraction who complete the full funnel |

And the metric that actually matters for ranking:

$$\text{Throughput} = f \times K$$

$f$ = trigger frequency (how often this behavior happens per eligible user per day).

---

# Loop 1: Job Sharing

HM or recruiter shares a job externally, bringing new prospects into the network.

```mermaid
graph LR
    Sharer["HM / Recruiter"] -->|"1. shares job link"| Job[Job]
    Job -.->|"2. link reaches"| Anon["External person"]
    Anon -->|"3. signs up"| NewUser["New Prospect"]
    NewUser -->|"4. expresses interest"| EOI[EOI]
    EOI -->|targets| Job
```

**Funnel:** Job shared -> Link viewed -> Viewer signs up -> Expresses interest

$$K_{sharing} = i_{share} \times c_{share}$$

- $i_{share}$ = people reached per share event
- $c_{share}$ = view-to-signup × signup-to-EOI

**Key insight:** Highest $i$ of any loop — each share reaches many people. Primary volume driver.

---

# Loop 2: Team Invite

HM or recruiter invites colleagues to collaborate, expanding the hiring side.

```mermaid
graph LR
    R["Recruiter"] -->|"1. creates job"| Job[Job]
    R -->|"2. designates as HM"| NewHM["New HM"]
    NewHM -->|"3. collaborates on"| Job
    NewHM -->|"4. reviews prospects"| EOI[EOI]
    NewHM -->|"5. creates own job"| Job2["New Job"]
```

**Funnel:** Invite sent -> Invite viewed -> Invitee signs up -> Collaborates on job

$$K_{team} = i_{invite} \times c_{invite} = c_{invite}$$

$i_{invite}$ is always 1 (each invite targets one person), so K equals the conversion rate.

**Key insight:** Variant B (recruiter pulls in new HM) is high-leverage — the HM arrives with a job already set up and lands directly in the review flow.

---

# Loop 3: Prospect Referral

A prospect shares a job or profile with peers, bringing new prospects in.

```mermaid
graph LR
    P1["Prospect"] -->|"1. shares job/profile"| Friend["Friend"]
    Friend -->|"2. signs up"| NewP["New Prospect"]
    NewP -->|"3. expresses interest"| EOI[EOI]
    EOI -->|targets| Job[Job]
```

**Funnel:** Prospect shares -> Friend views -> Signs up -> Expresses interest

$$K_{prospect} = i_{prospect} \times c_{prospect}$$

**Key insight:** This is a designed behavior. We need to instrument $f_{prospect}$ to learn if it happens naturally or requires product investment.

---

# Loop 4: Cross-Persona Bridge

A prospect later posts their own job, crossing from prospect side to hiring side.

```mermaid
graph LR
    P["User as Prospect"] -->|"was prospect on"| Job1["Job A"]
    P -->|"later creates (now HM)"| Job2["Job B"]
    Job2 -.->|"attracts"| NewP["New Prospects"]
```

**Not an $f \times K$ loop.** Measured as a period conversion rate:

$$\text{Bridge Rate} = \frac{D_{new}}{U_{single}}$$

$D_{new}$ = new dual-persona users in the period. $U_{single}$ = single-surface users.

**Key insight:** Most valuable loop — each bridge creates a new job that feeds Loops 1, 2, and 3. But no frequency lever. It depends on life circumstances (having an open role). The product lever is reducing friction, not increasing distribution.

---

# Loop 5: Custom Link Virality

A prospect's custom link in external applications pulls hiring contacts to Helix.

```mermaid
graph LR
    P["Prospect"] -->|"1. creates link"| CL["Custom Link"]
    P -->|"2. applies externally"| ExtJob["External Job"]
    ExtJob -.->|"3. hiring contact clicks"| CL
    CL -.->|"4. views profile"| ExtHM["External HM"]
    ExtHM -->|"5. signs up"| NewUser["New HM/Recruiter"]
    NewUser -->|"6. creates job"| Job2["Job on Helix"]
```

**Funnel:** Link created -> Used in application -> HM views profile -> Signs up -> Creates job

$$K_{custom} = i_{customlink} \times c_{customlink}$$

**Key insight:** Directly fed by Prospect Activation health metric — more CLs per prospect means more Loop 5 triggers. Brings in hiring-side users who then trigger Loops 1 and 2.

---

# Why throughput, not K

K-factor alone cannot rank loops:

| Loop | K | Trigger frequency ($f$) | Throughput ($f \times K$) |
|------|---|-------------------------|---------------------------|
| Loop A | 0.5 | 10/user/day | **5.0** |
| Loop B | 1.0 | 0.03/user/day | **0.03** |

Loop A produces **150x more growth** despite half the K-factor.

The dominant variable is **trigger frequency** — how often the underlying human behavior naturally occurs. The product can raise or lower $f$ at the margin, but the ceiling is set by the real-world activity.

---

# Loops compound through fan-out

A single node triggers multiple loop instances simultaneously:

```mermaid
graph TD
    subgraph prospectFanout ["Prospect Fan-Out"]
        P["Prospect"] -->|creates| CL1["Custom Link 1"]
        P -->|creates| CL2["Custom Link 2"]
        P -->|creates| CL3["Custom Link 3"]
        CL1 -.->|viewed by| Ext1["HM at Company A"]
        CL2 -.->|viewed by| Ext2["HM at Company B"]
        CL3 -.->|viewed by| Ext3["Recruiter at Company C"]
    end

    subgraph jobFanout ["Job Fan-Out"]
        P1["Prospect 1"] -->|EOI| EOI1["EOI 1"]
        P2["Prospect 2"] -->|EOI| EOI2["EOI 2"]
        P3["Prospect 3"] -->|EOI| EOI3["EOI 3"]
        EOI1 -->|targets| Job["Job"]
        EOI2 -->|targets| Job
        EOI3 -->|targets| Job
    end
```

In $K = i \times c$, the $i$ **is** the fan-out.

Loops amplify each other: Custom Link Virality brings in hiring-side users who trigger Job Sharing and Team Invite.

---

# What to instrument first

Prioritized by expected throughput impact:

| Priority | Loop | Primary metric to instrument | Why |
|----------|------|------------------------------|-----|
| 1 | **Job Sharing** | $f_{share}$ and $c_{share}$ | Broadest distribution surface; highest $i$ |
| 2 | **Custom Link** | $f_{customlink}$ and $c_{customlink}$ | Prospect-side viral engine; fed by Prospect Activation |
| 3 | **Team Invite** | $c_{invite}$ | Frequency bounded by team size; conversion is the lever |
| 4 | **Prospect Referral** | $f_{prospect}$ | Designed behavior; need to learn if it occurs naturally |
| 5 | **Cross-Persona Bridge** | Bridge rate, time-to-bridge | Each bridge creates a new job; friction is the lever |

---

# The full picture

```mermaid
graph TD
    HS["HELIX SIZE: (Uh x T) + (Up x EOI)"]
    HS --> Health["NETWORK HEALTH: Liquidity / Activation / Bridging"]
    Health --> Loops["VIRAL LOOPS: Throughput = f x K per loop"]
    Loops --> Funnels["FUNNELS: i and c decomposed into stages"]
    Funnels --> Events["INPUT EVENTS: What we track in analytics"]
```

**Helix Size** tells us how big the network is.

**Health metrics** tell us if the structure is sound.

**Loop throughput** ($f \times K$) tells us how fast it's growing — and which loops to invest in.

**Funnels** decompose $K$ into stages where users convert or drop off.

**Input events** are what we instrument. Every event rolls up through this hierarchy to Helix Size.
