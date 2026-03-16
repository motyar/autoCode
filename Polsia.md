# Polsia — AI That Runs Your Company While You Sleep
**(Adapted for Existing Project Integration)**

**Polsia** is a platform and system of autonomous AI agents that fully operates, scales, and manages entire online businesses 24/7 with little to no ongoing human involvement. It positions itself as an "AI co-founder" or "AI CEO" that handles planning, coding/engineering, marketing, sales/outreach, support, operations, analytics, ad management, and self-improvement for **existing projects**.

Founded by Ben Cera (former food company operator and CloudKitchens affiliate who taught himself coding via AI), it launched around late 2025/early 2026. As of mid-March 2026, it powers ~3,800+ active "company instances," has completed hundreds of thousands of tasks, sent 100k+ emails and 900+ tweets in a single day, and drives millions in combined annual run rate (ARR) across the ecosystem (platform metrics show rapid growth, e.g., $4M+ ecosystem ARR with 50%+ week-over-week spikes in some periods). Polsia itself runs autonomously and has scaled to high revenue (reports of $1M–$3M+ ARR for the platform in weeks/months) with zero human employees beyond Cera.

Users sign up at polsia.com (free to start, no credit card initially), connect their **existing project** (via repository link, current website, or API access), and Polsia audits the current state, maps the architecture, assumes control of the infrastructure, and starts running it. A morning summary email arrives; users can ignore it for full autopilot or reply to steer ("passive vs. active investor" mode). It handles edge cases like competitive research, bug fixes, and A/B testing ads or features on the existing codebase.

## Pricing & Business Model
* **Subscription:** ~$49/month base subscription (gets infrastructure management + 1 autonomous nightly task + credit budget for on-demand work).
* **Revenue Share:** Polsia takes a 20% revenue share from the companies it runs (to fund compute, scaling, and reinvestment). 
* **Ad Spend:** Ads spend is also involved (platform takes a cut or manages budgets). This creates a self-reinforcing "autonomous economy."

*Note: Polsia is not open-source. Public visibility comes from the live dashboard (polsia.com/live), founder interviews, Reddit analyses, and real-time terminal logs. It utilizes a proprietary multi-agent orchestration system with recurring LLM-powered cycles, tool-use, shared memory, and hierarchical decision-making.*

---

## High-Level Architecture

### Orchestration Layer
The central Polsia system provisions and manages thousands of isolated per-company "instances" or workspaces (e.g., Docker/VM-like environments at paths like `/opt/polsia/workspaces/company-XXXX`). For an existing project, it syncs with the current stack. Each instance gets its own:
* Connected environment mapped to the existing web app/codebase.
* Provisioned accounts/tools integrated with existing ones (email, virtual server, GitHub repo, Meta Ads, Twitter/X, Stripe/payments, OpenAI/Sora for video generation).
* Persistent state (DB, files, analytics).

### Agent Swarm
Not one monolithic AI but specialized autonomous agents (powered by frontier LLMs like Anthropic Claude Opus or OpenAI models via SDKs). 
* **CEO/Strategy Agent:** Oversees everything (nightly review).
* **Engineering Agent:** Codes, deploys, and fixes the *existing codebase* (access: web server, GitHub, DB, file system).
* **Marketing Agent:** Outreach, social, ads (access: email, Twitter, Meta Ads account; creates UGC).
* **Support Agent:** Handles user emails/inbox.
* **Platform Agent:** Prioritizes feature requests across all users via ticketing, builds improvements autonomously.
* **Sub-agents:** Specialized tools for research (browser), analytics, etc.

### Integrations & Tools
* LLM SDKs (OpenAI/Anthropic).
* Browser automation (Puppeteer/Chromium for scraping, QA, research, ad setup).
* File/code editing, email sending, ad APIs, tweet posting.
* Watchdog timers for stalled tasks.
* Shared "memory files" for cross-company learning.

### Hive Mind / Self-Improvement
Agents log learnings anonymously from every run ("what works/doesn't"). Polsia aggregates this into a collective memory (like a "hive brain") so the system improves faster than any single human or isolated agent. It builds new features for the platform based on common user requests.

### Autonomy Levels
80% AI operations ("the grind"); 20% human "taste" (creative direction via optional replies). Fully hands-off mode is supported.

---

## The Core Algorithm: Recurring Agent Cycles
This is the perpetual, event-driven or cron-like loop running 24/7 per company. It is hierarchical and agentic. 

### 1. Integration & Onboarding (One-Time per Existing Project)
* User connects their existing project/repository.
* LLM audits the existing codebase, reads the `README.md`, analyzes current web traffic/state, and maps the architecture.
* Spins up the workspace and integrates with the existing stack (e.g., Node/Express + Postgres).
* Provisions missing tools/accounts to complement the existing infrastructure.
* Establishes baseline metrics and prepares the first operational roadmap based on the current product state.

### 2. Observe / Perceive Phase (State Gathering)
* Pull real-time data: Site analytics (traffic, signups, purchases), ad performance (impressions, CTR, CPC, spend), inbox replies, existing code/files, tweets, support tickets, external web data.
* Browser/Puppeteer for competitive teardowns, QA testing of the live existing site, lead research.
* Periodic diagnostics: `flush_diagnostics`, `find /opt/polsia/workspaces/...`, listing files, searching code, watchdog checks ("3s since progress, active tool=none").

### 3. Plan / Reason Phase (CEO Agent Decision-Making)
* Nightly (or triggered): CEO agent analyzes state.
* Decides priority: "Best next step—refactor existing code? Marketing push? Support response?"
* Generates task list or actions. 
    * *Example:* "Mapping out touch sequence timing... Day 5 first follow-up... fire Touch 2 for overdue leads."
    * *Example:* "If existing ads don't perform, create second/third variant, turn off bad ones, increase budget on winners."
    * *Example:* Research competitors → create document ("Competitive Teardown: AI CRM Landscape").
* Treats non-replying users as "passive investors" → proceeds autonomously without assuming disinterest.

### 4. Execute Phase (Specialized Agents + Tools)
* Delegate to agents with direct tool access:
    * **Engineering:** Search/edit HTML/files/code in the *existing repository*, implement requested features, deploy, QA via browser.
    * **Marketing:** Research leads → send cold emails (daily limits, sequenced follow-ups), post tweets, create/run Meta ads (UGC videos via Sora/OpenAI: generate realistic pitching video, upload, target, monitor daily).
    * **Support/Other:** Respond to customer emails, update docs, manage infrastructure.
* On-demand extras via user credits (e.g., "Run Ads" one-click: agent auto-pitches company, generates video, sets campaign).
* Executes in parallel across companies (9k+ tasks/24h system-wide).

### 5. Evaluate / Adapt / Learn Phase
* Measure outcomes against the project's historical baseline (ARR growth, task completion, revenue).
* Kill losers / double down on winners (e.g., scale ad budget).
* Log learnings to shared memory files.
* Self-improve: Update strategies, prompts, or even platform features. "Polsia builds itself" — agents report needs (e.g., more compute) and act.

### 6. Maintenance / Loop Closure
* Watchdog ensures progress.
* Flush diagnostics, infrastructure management.
* Morning summary sent to user detailing optimizations made to the existing project; repeat nightly.
* Scales via hive mind: Learns across 10k–100k+ companies via trial-and-error + perfect recall.

---

## Live Evidence & Limitations
The `/live` page shows exactly this in real-time—terminal commands (managing infra, editing files, "Using browser...", "Task completed: Cold outreach..."), task lists, active company lists, recent docs/tweets/emails/ads table, and a metrics dashboard. 

**Self-Building & Meta Aspects:** Polsia was largely built by its own agents. It autonomously raises compute/funds by accessing inboxes or deciding needs. The platform agent prioritizes global improvements.

**Current Limitations:** Early users note UI bugs or average per-company revenue being modest initially. It relies on frontier LLMs, careful tool access, and the founder's architecture implementation. However, the system is explicitly built to adapt and improve itself continuously.
