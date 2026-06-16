# Rival IQ 

**AI-powered competitive intelligence for B2B sales teams.**

Rival IQ helps sales teams generate spec-level product comparisons and 
automated battlecards — turning raw product data into the kind of 
competitive insight that used to take hours of manual research.


## What it does

Sales teams ask natural-language questions ("how does our product compare 
to X on these specs?") and Rival IQ returns a structured comparison table 
alongside an AI-generated narrative — streamed in real time so the table 
appears instantly and the narrative builds token-by-token.

It also includes tooling for keeping competitive data fresh: an AI-powered 
research tool that audits whether tracked competitors are still current, 
and a discovery tool that finds and scores new competitor products for 
review before they're added to the database.


## Key design decisions

- **Streaming-first UX** — comparison results stream via Server-Sent Events 
  in phases (table → narrative → done), with mid-flight cancellation, so 
  the product feels responsive even with multi-second AI calls
- **Multiple output modes** — the same comparison data can be rendered as 
  a full comparison table, a short sales pitch, or a concise cheat sheet, 
  depending on what the sales context needs
- **Reliability built into the AI layer** — narrative results are cached 
  with a configurable TTL, and AI calls retry automatically on rate limits 
  before surfacing an error to the user
- **Right-sized models for each task** — different AI models are allocated 
  by task complexity (research audits vs. quick lookups vs. narrative 
  generation), balancing quality and cost
- **Human-in-the-loop data curation** — new competitor candidates are 
  scored for relevance by AI but require admin approval before entering 
  the database


## Tech stack

| Layer | Technology |
|---|---|
| Frontend | React · TypeScript · Vite · Tailwind |
| Backend | Express.js · TypeScript |
| Database | PostgreSQL · Drizzle ORM |
| AI | OpenAI API (multi-model allocation) |
| Auth | Session-based, role-based access control |


## Status

A proprietary application built and deployed for an enterprise client.
