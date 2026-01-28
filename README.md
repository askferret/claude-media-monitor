# Claude Media Monitor - Automated Intelligence System

[![Claude Code](https://img.shields.io/badge/Claude%20Code-Project-8A2BE2)](https://github.com/anthropics/claude-code)
[![Claude Code Projects Index](https://img.shields.io/badge/View-Claude%20Code%20Projects-blue)](https://github.com/danielrosehill/Claude-Code-Repos-Index)
[![Master Index](https://img.shields.io/badge/View-Master%20Index-green)](https://github.com/danielrosehill/Github-Master-Index)

Agent-native workspace for automated media monitoring, topic research, and signal generation. Transforms raw data into structured insights with complete provenance tracking.

## Purpose

This repository provides three core capabilities:

1. **Automated Topic Research**: Query broad topics (psychology, luxury, AI) with automated web searches and insight generation
2. **Media Monitoring**: Track coverage about specific subjects across publications with manual or automated workflows
3. **Signal Intelligence**: Transform articles and web data into structured signals with full citation trails

## Quick Start

### Automated Topic Research (New!)

**Query any broad topic for instant insights:**
```
/query psychology
/query luxury brands  
/query artificial intelligence regulation
```

This will:
- Execute automated web searches for latest data
- Fetch and save relevant articles
- Generate structured signals (trends, insights, patterns)
- Maintain complete provenance and citations
- Save everything to the database automatically

**No manual article selection required** - the system handles everything from search to insight.

### Traditional Media Monitoring

**For monitoring specific subjects, run setup first:**
```
/setup-monitoring
```

Then fetch articles manually:
```
/fetch [URL]
/batch [URL1] [URL2] [URL3]
```

### Analyze Your Data

**View generated signals:**
```
/signals
/signals --topic "psychology"
/signals --type trend
```

**Analyze article collection:**
```
/analyze
```

## Features

### Automated Query System (New!)

- **Native topic queries**: Research any broad topic with a single command
- **Automated web search**: System finds and retrieves latest relevant data
- **Signal generation**: Transforms raw data into structured insights (trends, patterns, opportunities)
- **Complete provenance**: Full citation trails and data lineage for every signal
- **No manual steps**: From query to insights, fully automated

### Signal Intelligence

- **Structured signals**: Trends, insights, patterns, anomalies, opportunities, risks
- **Confidence scoring**: Every signal includes confidence and relevance scores
- **Rich context**: Temporal, geographic, and industry context
- **Source attribution**: Complete tracking of all contributing articles and data sources
- **Searchable database**: Query signals by topic, type, date, or confidence level

### Article Organization

- **Date-based structure**: Articles organized by year and month (`/articles/YYYY/MM_MonthName/`)
- **Consistent naming**: `article_theme_DDMMYY_publication.md` format
- **Rich metadata**: Publication info, dates, authors, keywords, summaries
- **JSON schema validation**: Ensures data quality and consistency

### Available Commands

| Command | Description |
|---------|-------------|
| `/query` | **[NEW]** Automated topic research with signal generation |
| `/signals` | **[NEW]** View and search signal database |
| `/query-config` | **[NEW]** Manage query configurations and automation |
| `/setup-monitoring` | Configure monitoring context for specific subjects |
| `/fetch` | Fetch and save a single article |
| `/batch` | Process multiple articles at once |
| `/analyze` | Generate statistics and insights about your collection |
| `/search` | Search articles by keyword, publication, or date |
| `/stats` | Show collection statistics |
| `/validate` | Validate articles against schema |
| `/export` | Export articles in various formats (CSV, JSON) |
| `/profile-pub` | Research and profile a publication |

### Specialized Agents

Located in `.claude/agents/`:

- **query-orchestrator**: **[NEW]** Orchestrate automated topic research and signal generation
- **signal-generator**: **[NEW]** Generate structured insights from articles and data
- **article-fetcher**: Fetch and save individual articles with metadata
- **batch-fetch**: Process multiple articles efficiently
- **article-analyzer**: Analyze trends and generate reports
- **publication-profiler**: Research publication metadata and bias
- **archive-organizer**: Maintain archive quality and consistency

## Directory Structure

```
/articles/              # All fetched articles (organized by date)
  /YYYY/               # Year folders
    /MM_MonthName/     # Month folders
      article_*.md     # Individual article markdown files
/signals/              # [NEW] Generated signals (organized by date)
  /YYYY/               # Year folders
    /MM_MonthName/     # Month folders
      signal_*.json    # Signal data (JSON)
      signal_*.md      # Signal summaries (Markdown)
/queries/              # [NEW] Query configurations
  query_*.json         # Saved query configurations
/schemas/              # Data schemas and validation rules
  /fetched-article/
    fetch-schema.json       # JSON schema for article data
    fetch-instructions.md   # Detailed fetching guidelines
  /signal/             # [NEW] Signal schemas
    signal-schema.json      # JSON schema for signal data
  /query/              # [NEW] Query schemas
    query-schema.json       # JSON schema for query configs
/.claude/              # Claude Code configuration
  /agents/             # Specialized subagents
  /commands/           # Slash commands
/exports/              # Exported data (CSV, JSON, etc.)
/reports/              # Generated analysis reports
/publication-profiles/ # Publication metadata and profiles
```

## Data Schemas

### Article Schema

Each article includes:

**Required fields:**
- Title, publication name, URL
- Full text content and word count
- Claude-generated summary
- Classification (coverage/op-ed/by-subject)
- Keywords (5 tags)
- Display summary

**Optional enrichment:**
- Author information (name, title, bio)
- Publication details (summary, editorial leaning)
- Comment analysis (if article has comments)

See `/schemas/fetched-article/fetch-schema.json` for complete article schema.

### Signal Schema (New!)

Each signal includes:

**Required fields:**
- Signal ID, type (trend/insight/pattern/etc.), topic, title
- Summary and detailed analysis
- Confidence and relevance scores
- Source articles array (with URLs and contribution descriptions)
- Keywords and implications
- Complete provenance trail (collection method, processing steps, citations)
- Generation metadata (date, agent, query context)

**Optional enrichment:**
- Additional data sources beyond articles
- Temporal context (timeframe, velocity, emerging status)
- Geographic scope and industry sectors
- Related topics
- Priority and visibility settings

See `/schemas/signal/signal-schema.json` for complete signal schema.

### Query Configuration Schema (New!)

Query configurations define automated research:

- Query ID, name, type, and topic
- Search terms and scope (geographic, temporal, language)
- Data source configuration (web search, publications, archive)
- Processing instructions (signal types, confidence thresholds, focus areas)
- Automation settings (schedule, auto-save, notifications)
- Provenance configuration

See `/schemas/query/query-schema.json` for complete query schema.

## Workflow Examples

### Automated Topic Research (New!)

**Psychology Research Query:**
```
User: "/query psychology"

System:
1. Creates query configuration for "psychology" topic
2. Executes web searches: "psychology research", "psychological studies", "mental health developments"
3. Fetches top 15-20 relevant articles from past 60 days
4. Searches existing archive for related content
5. Analyzes all sources to identify patterns and trends
6. Generates 5-8 signals (trends, insights, developments)
7. Each signal includes:
   - Complete source attribution
   - Confidence and relevance scores
   - Full provenance trail with citations
8. Saves signals to /signals/2026/01_Jan/
9. Saves new articles to /articles/2026/01_Jan/
10. Produces comprehensive execution report

Result: Actionable intelligence with zero manual intervention
```

**Luxury Brands Intelligence:**
```
User: "/query luxury brands"

System:
1. Automated web search for luxury market trends, consumer behavior, brand strategy
2. Prioritizes recent articles (last 30 days)
3. Fetches 12-15 high-quality articles
4. Analyzes for trends, opportunities, patterns
5. Generates signals with geographic and industry context
6. Complete provenance: every claim traceable to sources
7. Ready-to-use insights with citations

Result: Market intelligence report with full data lineage
```

### Traditional Article Workflows

**Single Article Fetch:**
```
User: "Fetch this article: https://economist.com/example"
Claude: [Fetches, extracts, validates, saves to correct date folder]
```

**Batch Processing:**
```
User: "Fetch these 10 articles about climate policy"
Claude: [Processes all articles, provides summary report]
```

### Analysis
```
User: "/analyze the last month"
Claude: [Generates statistics, trends, topic breakdown]
```

### Search
```
User: "/search climate policy"
Claude: [Returns matching articles with metadata]
```

## Quality Standards

- **Content Quality**: Clean extraction, proper markdown formatting
- **Metadata Quality**: Accurate dates, authors, classifications
- **Organizational Quality**: Consistent naming and structure
- **Schema Compliance**: All articles validated against JSON schema

## Error Handling

The system gracefully handles:
- Paywall-protected articles
- Invalid URLs
- Missing metadata (uses sensible defaults)
- Publication date ambiguity
- Schema validation issues

## Integration

Works with Daniel's ecosystem:
- **MCP Servers**: Context7, Resend, Time
- **Notion**: Export summaries and reports
- **Obsidian**: Reference in notes
- **Analytics**: Export for visualization

## Best Practices

1. **Run `/setup-monitoring` first** - Establishes monitoring context
2. **Use batch operations** - More efficient for multiple articles
3. **Validate regularly** - Run `/validate` to check data quality
4. **Analyze periodically** - Generate insights with `/analyze`
5. **Profile publications** - Build metadata with `/profile-pub`
6. **Export for backup** - Use `/export` for data preservation

## Technical Details

- **Language**: Markdown for articles, JSON for schemas
- **Validation**: JSON Schema compliance checking
- **Organization**: Date-based hierarchical structure
- **Automation**: Specialized agents for complex workflows
- **Extensibility**: Add custom agents and commands as needed

## Getting Help

- Check `CLAUDE.md` for comprehensive system documentation
- Review `/schemas/fetched-article/fetch-instructions.md` for fetching guidelines
- Use `/stats` to understand your current collection
- Ask Claude for help with any command or workflow

## Version Control

This repository is designed to be version controlled. Commit logical groups of articles with clear messages:

```bash
git add articles/2025/11_Nov/
git commit -m "Add 15 climate policy articles from Nov 2025"
git push
```

---

**Ready to start?** Run `/setup-monitoring` to configure your media monitoring workspace.

---

To view an index of my Claude Code related projects, [click here](https://github.com/danielrosehill/Claude-Code-Repos-Index)
