# Setup & Use: Market Intelligence Automation

**Date:** 01/28/2026

This guide walks you through setting up and using the Claude Media Monitor skill set for automating market intelligence—from a first run to ongoing monitoring.

---

## What You Get

- **Automated topic research**: One command → web search, article fetch, analysis, and structured signals.
- **Structured signals**: Trends, insights, patterns, opportunities, risks—with confidence scores and full citations.
- **Provenance**: Every signal traces back to source articles and processing steps.
- **No separate app**: Everything runs inside Cursor/Claude Code; no `npm install` or env files required.

---

## 1. Setup (One-Time)

### 1.1 Workspace

- **Open this repo in Cursor** (or Claude Code) so the agent can see:
  - `CLAUDE.md` (system rules and structure)
  - `.claude/agents/` (query-orchestrator, signal-generator, article-fetcher, etc.)
  - `.claude/commands/` (slash commands)

No `package.json` or `.env` is required; the agents use the tools available in your Cursor session (e.g. web search, browser, MCP).

### 1.2 Optional: Define Your Monitoring Context

If you’re monitoring a **specific subject** (company, person, brand) and want that reflected in article tagging and analysis:

1. In chat, run: **`/setup-monitoring`**
2. Answer the prompts (subject, purpose, topics, publications, scope, relevance criteria).
3. The agent will **update `CLAUDE.md`** with your “Monitoring Subject Context” so future fetches and analyses use it.

You can skip this and still use topic-based queries; it’s only needed for subject-specific context.

---

## 2. Running Your First Market Intelligence Query

### Option A: Quick One-Off Topic

In Cursor chat, run:

```text
/query luxury brands
```

or any broad topic, e.g.:

```text
/query artificial intelligence regulation
/query psychology research
/query sustainable fashion
```

**What happens:**

1. A query configuration is created (or reused) for that topic.
2. The **query-orchestrator** agent runs web searches, fetches articles, and pulls from your archive if relevant.
3. Articles are saved under `/articles/YYYY/MM_MonthName/`.
4. The **signal-generator** produces structured signals (trends, insights, opportunities, etc.).
5. Signals are saved under `/signals/YYYY/MM_MonthName/` (JSON + Markdown).
6. You get an execution report (and optionally in `/reports/`).

No manual article selection; the pipeline is end-to-end.

### Option B: Use a Saved Query Config

Example configs are in `/queries/`:

- `example_luxury_brands.json`
- `example_ai_regulation.json`
- `example_psychology_research.json`

To run one:

```text
/query --config queries/example_luxury_brands.json
```

To create your own config and run it later:

```text
/query-config create "your market topic"
```

Then run it with:

```text
/query-config run qry_YYYYMMDD_identifier
```

(Replace with the actual `query_id` from the created file in `/queries/`.)

---

## 3. Viewing and Using Signals

### List and filter signals

```text
/signals
/signals --topic "luxury brands"
/signals --type trend
/signals --recent 30
```

### Inspect one signal

```text
/signals --id sig_20260128_150943_luxury
```

(Use the real signal ID from the list or from files in `/signals/`.)

### Where things live

| Output            | Location                          |
|------------------|-----------------------------------|
| Articles         | `/articles/YYYY/MM_MonthName/`    |
| Signals (data)    | `/signals/YYYY/MM_MonthName/*.json` |
| Signals (readable)| `/signals/YYYY/MM_MonthName/*.md`   |
| Query configs    | `/queries/*.json`                 |
| Reports          | `/reports/`                       |

---

## 4. Market Intelligence Workflows

### One-time market scan

```text
/query [your market or vertical]
```

Then:

```text
/signals --topic "[same topic]"
```

### Ongoing monitoring with a saved config

1. Create a config:  
   `/query-config create "e.g. luxury market trends"`
2. Optionally edit:  
   `/query-config edit qry_YYYYMMDD_id`
3. Run whenever you want:  
   `/query-config run qry_YYYYMMDD_id`

You can run the same config weekly or monthly (e.g. via a recurring Cursor session or external scheduler that triggers the agent).

### Competitive or regulatory tracking

Use or duplicate the AI regulation example:

```text
/query --config queries/example_ai_regulation.json
```

Then filter:

```text
/signals --topic "ai regulation" --type development
```

---

## 5. Customizing Query Configs

Edit any JSON in `/queries/` (or create via `/query-config create`). Important fields for market intelligence:

- **`search_terms`**: Keywords used for web search (e.g. "luxury market trends", "premium consumer behavior").
- **`search_scope.temporal.lookback_days`**: How far back to look (e.g. 30, 60).
- **`search_scope.geographic`**: e.g. `["Global", "Europe", "North America"]`.
- **`processing_instructions.signal_types`**: e.g. `["trend", "insight", "opportunity"]`.
- **`processing_instructions.min_confidence`**: Minimum signal confidence (e.g. 0.65).
- **`processing_instructions.focus_areas`**: e.g. "consumer behavior", "brand strategy", "market dynamics".

Schema reference: `/schemas/query/query-schema.json`.

---

## 6. Commands Cheat Sheet

| Command | Purpose |
|--------|--------|
| `/query [topic]` | Run automated research and signal generation for a topic |
| `/query --config queries/foo.json` | Run a saved query config |
| `/query-config create "topic"` | Create new query config |
| `/query-config list` | List saved configs |
| `/query-config run <query_id>` | Execute a saved config |
| `/signals` | List signals (optional filters: `--topic`, `--type`, `--recent`) |
| `/signals --id <id>` | Show one signal |
| `/setup-monitoring` | Set monitoring subject/context (updates CLAUDE.md) |
| `/fetch [URL]` | Fetch a single article (manual) |
| `/batch [URLs]` | Fetch multiple articles |
| `/analyze` | Archive stats and insights |
| `/search <keywords>` | Search articles |

---

## 7. Troubleshooting

- **“No /query command”**  
  Ensure this repo is open in Cursor and that `.claude/commands/query.md` is present. Slash commands are loaded from the workspace.

- **Few or no signals**  
  Broaden `search_terms`, increase `lookback_days`, or lower `min_confidence` in the query config.

- **Paywalled or missing articles**  
  The agent will note access issues in provenance; you can add more sources or use `/fetch` for specific URLs you can access.

- **Subject-specific tagging**  
  Run `/setup-monitoring` and fill in the subject and relevance criteria so `CLAUDE.md` is updated; the article-fetcher and analyzers use that context.

---

## 8. Next Steps

1. Run **`/query [your market topic]`** once and check `/signals` and `/articles`.
2. Copy an example from `/queries/` and adapt it to your vertical (search terms, scope, signal types).
3. Use **`/query-config create`** for topics you want to run repeatedly.
4. Use **`/setup-monitoring`** if you want a fixed “who/what we monitor” context in the repo.

For full system details, see **`CLAUDE.md`** and **`docs/QUERY_SYSTEM_GUIDE.md`**.
