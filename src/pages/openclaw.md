---
layout: ../layouts/MarkdownLayout.astro
title: 'Awesome Open CLAW Use Cases'
description: '50+ original use cases for Open CLAW — the personal AI assistant that lives in your messages, your terminal, your phone. Real ideas for real workflows.'
noIndex: false
permalink: /openclaw
---

<!--lint disable awesome-badge awesome-git-repo-age awesome-github awesome-toc-->

# Awesome Open CLAW Use Cases [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

> [Open CLAW](https://github.com/openclaw/openclaw) is a personal AI assistant that runs on your machine and talks to you on the channels you already use — WhatsApp, Telegram, Slack, Discord, Signal, iMessage, and [20+ more](https://docs.openclaw.ai/channels). It's a daemon, not an app.

## Contents

- [Developers and Engineers](#developers-and-engineers)
- [Founders and Business](#founders-and-business)
- [Personal Life](#personal-life)
- [Content Creators](#content-creators)
- [Teams and Work](#teams-and-work)
- [Health and Wellness](#health-and-wellness)
- [Education and Learning](#education-and-learning)
- [Finance and Planning](#finance-and-planning)
- [Communication and Relationships](#communication-and-relationships)
- [Automation and Smart Home](#automation-and-smart-home)

## Developers and Engineers

- **PR Review Digest** - Your agent watches GitHub repos and sends an evening summary of pending reviews, flagging risky changes and large diffs so you can prioritize.

  <details><summary>Scenario & how it works</summary>

  You push code all day. Reviews pile up. Set up your agent to watch your GitHub repos and send you a Slack DM every evening: "4 PRs need your review. The auth refactor is the big one — 847 lines, touches 12 files. The other three are under 50 lines each. Here are the key changes in each." Next morning, you review the summaries, click through the small ones quickly, and block time for the auth refactor.

  **How it works:** Cron job polls GitHub API every few hours. Agent summarizes diffs, flags risky changes (large files, security-sensitive paths, dependency updates). Delivers via whatever channel you're on. You respond in natural language and the agent posts review comments.

  </details>

- **On-Call Incident Commander** - When a page fires at 3 AM, your agent already has the alert context, checked the runbook, and queried recent deploys before you open your eyes.

  <details><summary>Scenario & how it works</summary>

  3 AM page. Your server's down. Instead of groggily opening five dashboards, your agent already has context. It pulled the alert from PagerDuty, checked the runbook, queried recent deployments, and texted you: "Looks like the Redis connection pool is exhausted. Last deploy was 2 hours ago by Sarah — added a new caching layer. Rollback command ready. Say 'rollback' or 'investigate more'."

  **How it works:** Webhook from your alerting tool triggers the agent. It uses browser and API skills to pull logs, correlate with deploy history, and check the runbook. Multi-channel means it can also post status updates to your team's Slack while talking to you on Signal.

  </details>

- **Dependency Drift Monitor** - Weekly scan of all your projects' dependencies with CVE alerts, breaking change analysis, and stale package warnings.

  <details><summary>Scenario & how it works</summary>

  Every Monday morning, your agent scans all your projects' dependencies. Not just "there's an update available" — it tells you "express 4.x → 5.0 is a major bump, here are the 3 breaking changes that affect your codebase. jsonwebtoken has a CVE published last Thursday. lodash hasn't been updated in 18 months — consider replacing the 2 functions you use."

  **How it works:** Cron-scheduled skill walks your package files, cross-references npm/PyPI/crates.io advisories, checks changelogs, and correlates with your actual import usage. Sends a structured report via Telegram or email.

  </details>

- **Log Whisperer** - Text your agent "why did the payment service crash at 2:47 PM?" and it SSHs in, greps logs, correlates traces, and texts you the root cause.

  <details><summary>Scenario & how it works</summary>

  "Why did the payment service crash at 2:47 PM?" You text this to your agent. It SSHs into your server, greps the logs around that timestamp, correlates with the request traces, and comes back with: "A null pointer in the webhook handler. Customer ID 4829 sent a payload missing the `currency` field. Your validation schema doesn't enforce it. Here's a fix."

  **How it works:** Agent has SSH access via configured skills. Understands your log format and can navigate your codebase. You interact from any channel — even your phone while walking to lunch.

  </details>

- **Architecture Decision Record Writer** - Agent reads Slack design discussions, extracts arguments and tradeoffs, and drafts a proper ADR in your team's format.

  <details><summary>Scenario & how it works</summary>

  You just finished a design discussion in Slack. Tell your agent "write up the ADR for the database migration decision." It reads the Slack thread, extracts the key arguments, identifies the decision and tradeoffs, and drafts a proper ADR in your team's format. Push it to your docs repo. You review and merge.

  **How it works:** Agent reads channel history (Slack/Discord skill), understands your ADR template from memory, generates the document, and creates a PR via GitHub API. All from a single message.

  </details>

- **Release Notes Generator** - Tag a release and your agent reads every commit, groups by type, writes human-readable descriptions, and posts to GitHub, Slack, and your changelog.

  <details><summary>Scenario & how it works</summary>

  Tag a release. Your agent reads every commit since the last tag, groups them by type (features, fixes, docs, internal), writes human-readable descriptions, identifies breaking changes, and posts the release notes to GitHub, Slack, and your changelog. No more "updated stuff" release notes.

  **How it works:** Git log parsing + commit message analysis. Agent understands conventional commits but also handles messy commit messages by reading the actual diffs. Cron or webhook triggered on tag push.

  </details>

- **Test Failure Explainer** - CI goes red and your agent messages you the root cause before you even click the build log — distinguishing real failures from flaky tests.

  <details><summary>Scenario & how it works</summary>

  CI goes red. Instead of clicking through to the build log, your agent already messaged you: "3 tests failed in the auth module. Two are the same root cause — you renamed `getUserById` to `findUser` but the mock factory still uses the old name. Third failure is a flaky timeout in the webhook integration test, been failing intermittently for 2 weeks."

  **How it works:** Webhook on CI failure → agent fetches build logs → parses test output → correlates with recent commits → classifies root cause. Knows your codebase well enough to distinguish real failures from flaky tests.

  </details>

## Founders and Business

- **Investor Update Writer** - Monthly cron pulls MRR from Stripe, users from PostHog, burn rate from your bank, and drafts an investor update in your voice.

  <details><summary>Scenario & how it works</summary>

  First of the month. Your agent pulls MRR from Stripe, active users from PostHog, burn rate from your bank feed, sprint velocity from Linear, and team headcount from your HR tool. Drafts an investor update in your voice. "MRR hit $47K, up 12% MoM. Shipped the enterprise SSO feature. Hired a senior backend engineer. Runway is 14 months." You tweak two sentences and send.

  **How it works:** Scheduled monthly cron. Agent queries multiple APIs, maintains a template based on your previous updates (stored in memory), and delivers the draft to your channel of choice. You reply with edits.

  </details>

- **Competitive Intelligence Radar** - Monitors competitor pricing pages, job postings, blogs, and changelogs, then sends you a weekly digest of meaningful changes.

  <details><summary>Scenario & how it works</summary>

  Your agent monitors your competitors' pricing pages, job postings, blog posts, and changelog feeds. Weekly digest: "Competitor A just launched a free tier. Competitor B posted 3 senior ML engineer jobs — likely building an AI feature. Competitor C hasn't shipped anything in 6 weeks." You see the landscape without checking 15 websites.

  **How it works:** Browser skill visits configured URLs on a schedule. Agent diffs pages against previous snapshots, identifies meaningful changes, filters noise. Stores history in memory for trend analysis.

  </details>

- **Customer Voice Synthesizer** - Aggregates support tickets, app reviews, NPS responses, and social mentions into a weekly sentiment synthesis.

  <details><summary>Scenario & how it works</summary>

  Support tickets, app store reviews, NPS responses, Twitter mentions — your customers talk to you in 10 different places. Your agent aggregates all of it and sends you a weekly synthesis: "Top 3 pain points this week: (1) onboarding flow confusion — 14 mentions, (2) export feature request — 8 mentions, (3) pricing page clarity — 6 mentions. Sentiment trending up vs. last week."

  **How it works:** Multi-source ingestion via API skills and browser scraping. NLP classification and clustering. Trend tracking via memory. Delivered as a structured report to Slack or email.

  </details>

- **Revenue Anomaly Detector** - Real-time monitoring that catches revenue drops within hours by comparing current metrics against historical baselines.

  <details><summary>Scenario & how it works</summary>

  Stripe webhook fires. Your agent notices something: "Revenue dropped 23% in the last 4 hours compared to this time last Tuesday. Churn is normal. Looks like new signups dropped — your landing page might be down." You check. It was. You saved hours of lost revenue because your agent noticed before you did.

  **How it works:** Webhook-driven real-time monitoring. Agent maintains rolling baselines in memory. Compares current metrics against historical patterns. Alerts immediately on significant deviations.

  </details>

- **Hiring Pipeline Narrator** - On-demand or scheduled ATS summaries showing candidate pipeline status, interview schedules, and stale roles that need attention.

  <details><summary>Scenario & how it works</summary>

  "Where do we stand on hiring?" you text your agent at 9 AM. It checks your ATS: "3 candidates in final round for the senior frontend role — interviews scheduled this week. The DevOps role has 12 new applicants, 4 look strong. The design role has been open 6 weeks with no good candidates — consider adjusting the job description or trying a different channel."

  **How it works:** ATS API integration (Greenhouse, Lever, Ashby). Agent queries on demand or via scheduled reports. Tracks pipeline velocity and flags stale roles.

  </details>

## Personal Life

- **Grocery Autopilot** - Share a recipe link and your agent extracts ingredients, checks your pantry memory, and sends the missing items list organized by store section.

  <details><summary>Scenario & how it works</summary>

  You share a recipe link in WhatsApp: "making this tonight." Your agent extracts the ingredients, checks them against what you already have (you told it last week), and adds the missing items to your grocery list. Friday afternoon it sends you the consolidated list: "You need: heavy cream, thyme, 2 lemons, arborio rice." Organized by store section.

  **How it works:** Web scraping for recipe extraction. Memory-based pantry tracking (you tell it what you bought, it maintains the list). Scheduled weekly summary + on-demand additions. Delivered to whichever channel you use for personal stuff.

  </details>

- **Travel Planner** - Describe your dream trip in natural language and your agent researches flights, builds a day-by-day itinerary, and delivers it as a Canvas visualization.

  <details><summary>Scenario & how it works</summary>

  "I want to go to Lisbon in March for 5 days. Budget around $2K. I like walking neighborhoods, eating at local spots, and avoiding tourist traps." Your agent researches flights, hotels near interesting neighborhoods, builds a day-by-day itinerary with restaurant suggestions, and checks visa requirements. It delivers the whole plan as a Canvas visualization. You tweak it over the next week via chat.

  **How it works:** Browser skill for flight/hotel research. Memory for your travel preferences (learned from past trips). Canvas for visual itinerary presentation. Ongoing conversation for refinements.

  </details>

- **School Portal Watcher** - Daily scrapes of your kids' school portals with a calm summary of grades, due dates, and upcoming events.

  <details><summary>Scenario & how it works</summary>

  School portal updates grades at random times. Your agent checks it daily and sends you a calm summary: "Mia got an A on the math test. Jake's history essay is due Friday — he hasn't submitted it yet. Parent-teacher conference slots opened up, the good times go fast." No more logging into three different school portals.

  **How it works:** Browser skill with saved login credentials (stored securely in your workspace). Daily cron scrapes portal pages, diffs against previous state, highlights actionable items. Multi-child support across different school systems.

  </details>

- **Home Maintenance Tracker** - Tracks when you last did maintenance tasks, proactively reminds you based on manufacturer timelines, and answers "when did I last…?" questions.

  <details><summary>Scenario & how it works</summary>

  "When did I last change the HVAC filter?" you text your agent. "October 14. That's 139 days ago. Manufacturer recommends every 90 days. You should change it this weekend." It also proactively reminds you: gutters before fall, smoke detector batteries twice a year, water heater flush annually. All tracked, all timed to your specific home.

  **How it works:** Memory-based tracking. You tell it things naturally ("changed the furnace filter today") and it logs them. Cron-scheduled proactive reminders based on manufacturer guidelines and your home's specifics.

  </details>

- **Package Delivery Tracker** - Watches your email for shipping confirmations, extracts tracking numbers, monitors carriers, and consolidates all delivery statuses in one place.

  <details><summary>Scenario & how it works</summary>

  Your agent watches your email for shipping confirmations. When it spots one, it extracts the tracking number and monitors delivery status. "Your Amazon order is out for delivery — ETA 2-4 PM. The guitar strings from Reverb shipped yesterday, arriving Thursday. The return you sent back was received by the warehouse today." All in one place, zero effort.

  **How it works:** Gmail Pub/Sub integration monitors incoming emails. Agent extracts tracking numbers via pattern matching, queries carrier APIs, and consolidates status updates. Alerts you on delivery day.

  </details>

- **Weather-Aware Day Planner** - Morning briefing that cross-references your calendar with the weather forecast and adjusts your outdoor plans automatically.

  <details><summary>Scenario & how it works</summary>

  6:30 AM. Your agent checks the weather and your calendar. "Rain starts at 2 PM. You have an outdoor lunch at 12:30 — you'll be fine, but bring an umbrella for the walk back. Your 4 PM run should move to morning. Tomorrow looks clear." It knows your habits because you told it about them once.

  **How it works:** Weather API + calendar integration + memory of your routines. Correlates outdoor activities with forecast. Delivered as a morning message before you even think to check.

  </details>

- **Birthday and Gift Assistant** - Reminds you of upcoming birthdays with gift ideas based on the person's interests, your past gifts, and nearby stores.

  <details><summary>Scenario & how it works</summary>

  Two days before your friend's birthday, your agent reminds you. But it goes further: "Sarah turns 35 on Thursday. Last year you got her a cookbook. She's been posting about pottery classes lately. The studio near her apartment does gift cards — here's the link." You click through and order it yourself in 30 seconds.

  **How it works:** Contact date tracking in memory. Social media monitoring (optional) for interest signals. Purchase history in memory to avoid repeats. E-commerce browsing via browser skill for gift suggestions and direct links.

  </details>

- **Subscription Audit** - Monthly report of all active subscriptions with total spend, unused services flagged, and price changes detected.

  <details><summary>Scenario & how it works</summary>

  First of each month: "You have 23 active subscriptions totaling $847/month. Three you haven't used in 90+ days: Figma ($15), MasterClass ($15), that meditation app ($13). The Spotify family plan went up $2 last month. Here's the full breakdown." Finally, clarity on where your money goes.

  **How it works:** Bank feed integration or manual subscription logging. Agent tracks usage signals (email receipts, login frequency from email notifications). Monthly cron delivers the report.

  </details>

## Content Creators

- **Newsletter Ghostwriter** - Synthesizes your weekly bookmarks, notes, and highlights into a newsletter draft that matches your voice and structure.

  <details><summary>Scenario & how it works</summary>

  All week you save bookmarks, highlight tweets, jot quick notes. Thursday evening, your agent synthesizes everything into a newsletter draft: introduction that ties the themes together, three main sections with your annotations, a "quick links" footer. It knows your voice because it's read every issue you've ever sent. You spend 20 minutes editing instead of 3 hours writing.

  **How it works:** Memory accumulates your saves and notes throughout the week. Cron triggers Thursday evening. Agent reads your past newsletters from memory to match tone and structure. Delivers draft to your channel for review.

  </details>

- **Video Essay Research Companion** - Tell your agent a video topic and within 24 hours get a structured outline with academic sources, expert quotes, and footage timestamps.

  <details><summary>Scenario & how it works</summary>

  You're planning a video on "why cities keep building ugly buildings." Tell your agent. Over the next 24 hours, it researches: academic papers on urban planning incentives, notable examples with before/after photos, expert quotes, counterarguments. Delivers a structured outline with sources and timestamps for where to find key footage. You'd have spent a week doing this manually.

  **How it works:** Browser skill for deep web research. Academic search via Google Scholar. Agent structures findings into your preferred outline format. Delivers as a Canvas document you can rearrange.

  </details>

- **Social Media Calendar** - Generate a week of platform-specific post ideas with hooks, threads, and optimal posting times based on your audience data.

  <details><summary>Scenario & how it works</summary>

  Instead of staring at a blank content calendar, tell your agent your goals: "grow developer audience, promote the new course, stay relevant in the AI conversation." It generates a week of post ideas with hooks, threads, and suggested posting times based on when your audience is most active. Each morning, it sends you today's draft. You tweak and post.

  **How it works:** Memory stores your audience data, past performance, and content pillars. Agent analyzes trending topics via browser skill. Generates posts calibrated to platform (different formats for X vs. LinkedIn vs. Threads). Cron delivery on your schedule.

  </details>

- **Podcast Show Notes Generator** - Drop an audio file and get timestamped chapters, key quotes, a summary, guest bio, and a promo tweet thread in minutes.

  <details><summary>Scenario & how it works</summary>

  Record your episode. Drop the audio file to your agent. Within minutes: timestamped chapter markers, key quotes pulled out, a two-paragraph summary, guest bio compiled from their website, and a tweet thread promoting the episode. What used to take 2 hours of post-production takes 2 minutes of review.

  **How it works:** Audio transcription via built-in media pipeline. Agent identifies topics and transitions for chapter markers. Browser skill pulls guest info. Formats output for your publishing platform.

  </details>

- **Trend Spotter** - Monitors HackerNews, Reddit, X, and niche forums to identify rising topics before they peak, filtered for your specific audience.

  <details><summary>Scenario & how it works</summary>

  "What should I make content about this week?" Your agent monitors HackerNews, Reddit, X, and your niche forums. It identifies rising topics before they peak: "Edge computing discussions are up 340% this week. Three popular posts about SQLite replacing Postgres for small projects. A new open-source alternative to Vercel just launched and people are excited." You're always early to the conversation.

  **How it works:** Multi-source monitoring via browser skill and API integrations. Agent tracks velocity of topic mentions over time, compares against baseline. Filters for your specific niche. Weekly or on-demand delivery.

  </details>

## Teams and Work

- **Self-Running Standup** - Messages each team member on their preferred channel, collects responses, identifies overlapping blockers, and posts a compiled summary.

  <details><summary>Scenario & how it works</summary>

  9:05 AM. Your agent messages each team member on their preferred channel: "What did you ship yesterday? What's the plan today? Anything blocking you?" Collects responses, identifies blockers that overlap, and posts a compiled standup summary to the team Slack. If someone doesn't respond by 9:30, it sends a gentle nudge.

  **How it works:** Multi-channel routing — each person gets the message where they actually respond (some prefer Telegram, others Slack, one person uses iMessage). Agent aggregates responses, identifies common themes, posts summary. Cron-driven daily.

  </details>

- **Meeting Prep Brief** - 30 minutes before any meeting, get a brief with last meeting notes, open tickets, usage trends, and unfulfilled promises for each attendee.

  <details><summary>Scenario & how it works</summary>

  You have a meeting with a client in 30 minutes. Your agent sends you a brief: "Last meeting was Jan 15 — they asked about API rate limits and you promised to follow up (you didn't). They have 3 open support tickets. Their usage went up 40% last month. Their contract renews in 6 weeks." You walk in prepared.

  **How it works:** Calendar integration detects upcoming meetings. Agent cross-references attendees with your CRM, support tool, and previous meeting notes stored in memory. Delivers brief 30 minutes before start time.

  </details>

- **Knowledge Base Auditor** - Weekly comparison of your team docs against the actual codebase, flagging outdated guides and missing API references.

  <details><summary>Scenario & how it works</summary>

  Your team docs are always outdated. Set up your agent to compare documentation against the actual codebase weekly. "The authentication guide still references the old JWT flow — you switched to session tokens 3 months ago. The deployment docs mention a staging server that no longer exists. The API reference is missing 4 endpoints added in the last sprint."

  **How it works:** Cron-scheduled comparison between docs content and actual code/config. Agent identifies discrepancies using code analysis skills. Reports specific files and sections that need updating, with suggested corrections.

  </details>

- **Cross-Timezone Coordinator** - Timezone-aware handoff briefings that tell each team what happened while they slept and what needs attention today.

  <details><summary>Scenario & how it works</summary>

  Your team spans San Francisco, London, and Tokyo. Your agent knows everyone's working hours and manages handoffs: "The Tokyo team finished the API changes and left notes. London reviewed and found two issues — logged in Linear. Here's what needs your attention when you start today." Each timezone gets a tailored briefing when their day begins.

  **How it works:** Timezone-aware cron scheduling. Agent monitors project management tools for updates, filters by relevance to each timezone's team members, and delivers personalized briefings at each team's start-of-day.

  </details>

- **Decision Log Keeper** - Watches team channels for decisions, extracts the what/who/why/when, and maintains a searchable decision archive.

  <details><summary>Scenario & how it works</summary>

  Decisions happen in Slack threads, Zoom calls, hallway conversations. They get lost. Tell your agent every time a decision is made — or better, it watches your channels and identifies decisions automatically. "Decision: We're using Postgres, not MySQL. Decided by: CTO. Reason: team expertise. Date: March 1." Searchable forever.

  **How it works:** Passive monitoring of team channels (with appropriate permissions). Agent identifies decision-language patterns. Confirms with the relevant person. Stores in structured memory. Queryable: "what did we decide about the database?"

  </details>

## Health and Wellness

- **Adaptive Fitness Program** - Daily workout plans that adjust based on your reported soreness, sleep quality, and energy levels from yesterday.

  <details><summary>Scenario & how it works</summary>

  Your agent knows your workout plan. Monday morning: "Today is squat day. You mentioned your left knee was sore yesterday, so I've swapped barbell squats for leg press and added extra quad stretches. Projected session: 55 minutes." After your workout, you text "done, knee felt fine actually" and it adjusts tomorrow's plan accordingly.

  **How it works:** Workout plan stored in memory. Agent tracks your reported soreness, sleep, and energy levels. Modifies exercises based on a set of substitution rules and your feedback loop. Delivered daily before your usual gym time.

  </details>

- **Sleep Pattern Analyzer** - Weekly correlation of your sleep data with calendar events, habits, and activities to surface actionable insights.

  <details><summary>Scenario & how it works</summary>

  You wear a fitness tracker. Your agent ingests the sleep data weekly and correlates it with everything else: "You average 6.2 hours this month, down from 6.8 last month. Your worst nights correlate with late meetings (after 7 PM) and screen time past 11 PM. Best sleep happens when you run in the morning." Actionable, not just data.

  **How it works:** Health data integration via Apple Health exports or API. Agent maintains rolling statistics in memory. Correlates with calendar events, activity logs, and your reported habits. Weekly insight delivery.

  </details>

- **Meal Logger and Nutrition Tracker** - Photograph your meal, get a calorie and macro estimate, and see running daily totals with practical suggestions to hit your targets.

  <details><summary>Scenario & how it works</summary>

  You photograph your lunch and send it to your agent. "Grilled chicken salad with avocado, about 500 calories, 40g protein." End of day: "You're at 1,850 calories, 120g protein, 65g fat. You're 30g short on protein — a Greek yogurt before bed gets you there." No app to open, no food to search for. Just text a photo.

  **How it works:** Image analysis via vision-capable model. Agent maintains daily running totals in memory. Knows your targets because you told it once. Suggests corrections based on what's practical, not theoretical.

  </details>

- **Medication and Supplement Tracker** - Text-based medication logging with missed-dose reminders, interaction warnings, and monthly adherence reports.

  <details><summary>Scenario & how it works</summary>

  "Taking my vitamins" you text at 8 AM. Your agent logs it. If you forget, it reminds you at 9:30 AM. When you add a new supplement, it checks for interactions with your current stack. Monthly report: "You've been consistent 26 out of 30 days. The magnesium + zinc you're taking might compete for absorption — consider taking them at different times."

  **How it works:** Simple text-based logging stored in memory. Interaction checking via health databases (browser skill). Adherence tracking with gentle reminders via cron. No app needed — just your messages.

  </details>

- **Therapy Session Prep** - Compiles a private weekly brief of your mood patterns, stressors, and positive moments to help you prepare for therapy appointments.

  <details><summary>Scenario & how it works</summary>

  Before your weekly therapy appointment, your agent compiles a brief for you (not your therapist — for your own reference): "This week you mentioned feeling overwhelmed on Tuesday and Thursday. The trigger both times was work deadlines. You slept poorly those nights. You had two really good days — Wednesday after your run and Saturday with friends." Helps you make the most of your session.

  **How it works:** You explicitly opt in and log mood entries throughout the week — the agent only analyzes what you send it directly. All data stays local on your machine (Open CLAW is local-first by design). Delivers a personal summary the morning of your appointment. Note: review your local health data regulations before tracking personal wellness data.

  </details>

## Education and Learning

- **Spaced Repetition Tutor** - Daily flashcards via Telegram with voice input support, adaptive intervals, and weekly progress reports on your weak areas.

  <details><summary>Scenario & how it works</summary>

  You're learning Spanish. Your agent sends you 10 flashcards via Telegram at breakfast. You answer by voice. It tracks your accuracy, adjusts intervals — words you know well appear less often, tricky ones come back the next day. "You've mastered 340 words. Your weakest area is subjunctive conjugations. Tomorrow I'll focus on those."

  **How it works:** Spaced repetition algorithm running in the agent's memory. Cards generated from your learning material. Voice input via Talk Mode for pronunciation practice. Adaptive scheduling via cron.

  </details>

- **Paper Reading Group Organizer** - Summarizes dropped arXiv links, generates discussion questions, cross-references past papers, and delivers prep packages before meetings.

  <details><summary>Scenario & how it works</summary>

  Your research group reads one paper per week. Members drop arXiv links into the group chat. Your agent summarizes each paper, generates 5 discussion questions, identifies connections to papers you've read before, and sends the prep package 24 hours before the meeting. After the meeting, it archives the discussion notes.

  **How it works:** Group chat monitoring for paper links. Browser skill fetches and parses papers. Agent generates structured summaries. Memory maintains reading history for cross-references. Cron delivers prep materials.

  </details>

- **Learn-in-Public Accountability Partner** - Daily check-ins tracking your learning progress against a personalized plan, with adaptive scheduling when you fall behind.

  <details><summary>Scenario & how it works</summary>

  You committed to learning Rust. Your agent checks in daily: "Day 14 of your Rust journey. Yesterday you completed the ownership chapter. Today's suggested exercise: implement a linked list. You're 40% through your 30-day plan." If you skip a day, it adapts the schedule. If you skip three days, it asks what's going on.

  **How it works:** Learning plan stored in memory with daily milestones. Progress tracked via your check-ins. Agent adapts pace based on actual progress vs. plan. Daily delivery via your preferred channel.

  </details>

- **Conference Talk Prep Coach** - Analyzes your talk outline for pacing, researches similar presentations, and generates practice Q&A sessions over the weeks leading up to your talk.

  <details><summary>Scenario & how it works</summary>

  You're giving a talk in 3 weeks. Your agent helps you prepare: "Based on your outline, your talk runs about 35 minutes. The section on caching is dense — consider splitting it into two parts with a demo in between. I found 3 recent talks on similar topics — here are the angles they took so you can differentiate. Want me to generate a practice Q&A?"

  **How it works:** You share your outline and talk details. Agent analyzes pacing, identifies areas that need more/less depth, researches similar talks via browser skill. Generates practice questions. Tracks your preparation progress over the weeks.

  </details>

- **Textbook Companion** - After each chapter, your agent explains confusing concepts differently, generates practice problems, and connects ideas across chapters.

  <details><summary>Scenario & how it works</summary>

  You're working through a dense textbook. After each chapter, you tell your agent what confused you. It explains it differently, generates practice problems, and connects concepts to things you already know. "Chapter 7's explanation of backpropagation assumes you understood the chain rule from Chapter 3. Here's the connection they didn't make explicit."

  **How it works:** Memory maintains your learning context — what you've covered, what confused you, your background knowledge. Agent generates explanations tailored to your level. Creates practice problems with step-by-step solutions.

  </details>

## Finance and Planning

- **Tax Season Auto-Organizer** - Forward receipts and 1099s year-round, and your agent categorizes, totals, and identifies missing documents come January.

  <details><summary>Scenario & how it works</summary>

  Throughout the year, whenever you get a receipt, a 1099, a donation acknowledgment — you forward it to your agent. It categorizes everything: business expense, medical, charitable, investment. Come January: "Your tax documents are organized. 147 items across 8 categories. Total deductible business expenses: $23,400. You're missing the 1099 from your freelance client in Q3 — want me to draft a reminder email?"

  **How it works:** Email forwarding or photo-based receipt capture. Agent categorizes using tax rules stored in memory. Maintains running totals. Generates year-end summary with gaps identified. All data stays local.

  </details>

- **Real Estate Scout** - Daily monitoring of listing sites with intelligent matching that understands "good schools" and "quiet street," not just bedroom count.

  <details><summary>Scenario & how it works</summary>

  "Find me a 3-bedroom house in Austin under $500K with a garage and good schools." Your agent monitors Zillow and Redfin daily. When a match appears: "New listing at 1847 Oak Street. $485K, 3BR/2BA, 1,800 sqft. School rating 8/10. Commute to your office: 22 minutes. Listed 2 hours ago — these go fast." You reply "schedule a showing" and it drafts the email to the realtor.

  **How it works:** Browser skill monitors listing sites with your saved search criteria. Agent evaluates each listing against your stated priorities (not just filters — it understands "good schools" and "quiet street"). Alerts immediately on strong matches.

  </details>

- **Freelance Invoice and Payment Tracker** - Tracks invoices, flags overdue payments with client patterns, drafts follow-up emails, and maintains your running P&L.

  <details><summary>Scenario & how it works</summary>

  You send an invoice. Your agent tracks it. 30 days later: "Invoice #047 to Acme Corp is overdue. Originally due Feb 15. Amount: $4,200. This is their third late payment in a row. Want me to draft a follow-up email?" It also maintains your running P&L: "February revenue: $12,800. Outstanding: $7,400. Average days to payment: 34."

  **How it works:** You tell the agent when you send invoices and when payments arrive. It maintains the ledger in memory, tracks payment patterns per client, generates follow-up reminders via cron, and provides financial summaries on demand.

  </details>

- **Investment Portfolio Narrator** - On-demand or weekly portfolio summaries with benchmark comparison, allocation drift alerts, and rebalancing suggestions.

  <details><summary>Scenario & how it works</summary>

  "How are my investments doing?" Your agent checks your portfolio: "Your total is up 3.2% this month. The S&P 500 is up 2.1%, so you're outperforming. Your biggest winner is the semiconductor ETF (+8.4%). Your crypto allocation drifted to 12% of your portfolio — your target was 10%. The bond fund you bought in January is down 1.2%, which is expected with rate movements."

  **How it works:** API integration with your brokerage or manual position tracking in memory. Agent maintains your target allocation, tracks performance against benchmarks, and identifies when rebalancing is needed. On-demand or weekly reports.

  </details>

## Communication and Relationships

- **Language Practice Partner** - Daily conversations in your target language that adapt to your level, with weekly vocabulary and grammar accuracy reports.

  <details><summary>Scenario & how it works</summary>

  Every morning at 8 AM, your agent starts a conversation with you in French. It adapts to your level — if you're struggling, it simplifies. If you're flowing, it challenges you with idioms and complex tenses. End of week: "You had 5 conversations this week. Vocabulary used: 420 unique words (up from 380 last week). Grammar accuracy: 78%. Biggest improvement: past tense. Focus area: subjunctive mood."

  **How it works:** Daily cron-triggered conversation via Telegram. Agent maintains your vocabulary list, grammar accuracy stats, and level progression in memory. Uses voice mode for pronunciation practice. Adapts difficulty dynamically.

  </details>

- **Group Trip Planner** - Manages group chat polls, collects preferences across timezones, researches matching destinations, and presents consolidated options with cost breakdowns.

  <details><summary>Scenario & how it works</summary>

  8 friends. 3 timezones. 47 opinions. Your agent manages it: polls the group chat for date preferences, collects budget ranges, researches destinations that match constraints, and presents 3 options with cost breakdowns. "Option A: Lisbon, $1,200/person including flights. Option B: Mexico City, $900/person. Option C: Montreal, $800/person. Vote by replying A, B, or C."

  **How it works:** Group chat integration. Agent tracks responses, manages polls, and handles the inevitable "wait, can we do the week after instead?" changes. Presents consolidated options and manages the decision process without anyone being the "organizer."

  </details>

- **Networking Follow-Up System** - Stores conference contacts with conversation context, schedules follow-up reminders, and drafts personalized messages.

  <details><summary>Scenario & how it works</summary>

  You meet someone at a conference. You text your agent: "Met Sarah Chen, VP of Engineering at Stripe. Talked about our API design challenges. She's interested in our approach to rate limiting." Three days later, your agent reminds you: "Follow up with Sarah Chen. Draft: 'Great meeting you at the conference. I put together those notes on our rate limiting approach — happy to jump on a quick call.'"

  **How it works:** Contact + context stored in memory. Cron-scheduled follow-up reminders. Agent drafts personalized messages based on the original conversation context. Tracks the relationship over time.

  </details>

- **Family Communication Hub** - Bridges family members across WhatsApp, iMessage, Telegram, and more — one message from you reaches everyone on their preferred channel.

  <details><summary>Scenario & how it works</summary>

  Your aging parents aren't on Slack. Your sister uses WhatsApp. Your brother only checks iMessage. Your agent bridges them all: share a photo in WhatsApp and tell your agent "send this to the family." It forwards to each person on their preferred channel. Family announcement? One message, five channels. No one gets left out because they don't use the "right" app.

  **How it works:** Open CLAW's multi-channel architecture is literally built for this. Agent maintains a contact → channel mapping. Message forwarding with format adaptation (some channels support images differently). Group coordination across platforms.

  </details>

## Automation and Smart Home

- **Energy Usage Optimizer** - Analyzes smart home data, correlates usage spikes with your schedule and weather, and suggests (or executes) optimizations.

  <details><summary>Scenario & how it works</summary>

  Your smart home generates data. Your agent makes sense of it: "Your electricity bill is trending 15% higher than last month. The biggest change is the HVAC running 3 extra hours daily since you lowered the thermostat to 68°F. Suggestion: set it to 70°F during work hours when you're not home, save an estimated $40/month." It can even adjust the thermostat if you connect a smart home API.

  **How it works:** Smart home API integration (Home Assistant, SmartThings). Agent analyzes usage patterns, correlates with weather data and your schedule, and suggests optimizations. Can execute changes with your approval.

  </details>

- **Digital Estate Manager** - Monitors account expirations, breached passwords, expiring credit cards, and stale API tokens across your 200+ online accounts.

  <details><summary>Scenario & how it works</summary>

  You have 200+ online accounts. Your agent helps you maintain them: "3 accounts are using passwords from the 2019 breach. Your domain registration expires in 45 days. The credit card on file for AWS expires next month. Your GitHub personal access token expires in 2 weeks." It's the maintenance work no one does until something breaks.

  **How it works:** Password manager integration or manual account tracking in memory. Agent monitors expiration dates, checks breach databases, and tracks upcoming renewals. Proactive alerts via cron.

  </details>

## Getting Started

```sh
npm install -g openclaw@latest
openclaw onboard --install-daemon
```

Pick one use case from this list. Set it up. Live with it for a week. Then add another.

## Resources

- [Open CLAW on GitHub](https://github.com/openclaw/openclaw) - Source code and releases.
- [Documentation](https://docs.openclaw.ai) - Full docs for setup, channels, skills, and configuration.
- [Getting Started Guide](https://docs.openclaw.ai/start/getting-started) - Step-by-step first install.
- [Discord Community](https://discord.gg/clawd) - Chat with the community and get help.

## Contributing

Contributions welcome. If you build something interesting with Open CLAW, add it here.
