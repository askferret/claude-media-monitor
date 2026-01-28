# Automated Query System - Usage Guide

## Overview

The automated query system transforms topic research from a manual, multi-step process into a single-command operation. Query any broad topic and receive structured insights with complete provenance tracking.

## Quick Start

### Basic Topic Query

Simply query any broad topic:

```
/query psychology
/query luxury brands
/query artificial intelligence regulation
```

The system will:
1. Execute automated web searches for latest data
2. Fetch and save relevant articles
3. Analyze content for patterns and trends
4. Generate structured signals (insights, trends, developments)
5. Save everything with complete provenance tracking

### View Generated Signals

```
/signals
```

List all signals with summary information.

### Filter Signals

```
/signals --topic "psychology"
/signals --type trend
/signals --recent 30
```

### View Specific Signal

```
/signals --id sig_20260128_150943_ai_regulation
```

Shows complete signal details including full analysis, sources, scores, and provenance.

## Example Workflows

### Workflow 1: Quick Topic Research

**Goal**: Research psychology developments from the past 2 months

```bash
# Execute query
/query psychology

# System executes:
- Web searches for psychology research, studies, developments
- Finds 18 relevant articles from past 60 days
- Fetches and saves to /articles/2026/01_Jan/
- Analyzes content across all sources
- Generates 7 signals (trends, insights, developments)
- Saves signals to /signals/2026/01_Jan/

# View results
/signals --topic "psychology"
```

### Workflow 2: Ongoing Market Intelligence

**Goal**: Monitor luxury market trends weekly

```bash
# Create query configuration
/query-config create "luxury market trends"

# Configure for weekly automated execution
# Run immediately
/query-config run qry_20260128_luxury

# System executes every Monday at 9 AM automatically
```

### Workflow 3: Competitive Intelligence

**Goal**: Track AI regulation developments globally

```bash
# Use pre-configured query
/query-config run qry_20260128_ai_regulation

# System analyzes AI regulation across multiple regions
# Generates development and risk signals
# Includes geographic context

# Review results
/signals --type development --topic "ai regulation"
```

## Understanding Signals

### Signal Types

- **Trend**: Directional movement over time
- **Insight**: Non-obvious observation
- **Pattern**: Recurring theme across sources
- **Anomaly**: Unexpected development
- **Opportunity**: Potential for action
- **Risk**: Potential threat
- **Development**: New or emerging situation

### Confidence Scores (0.0 - 1.0)

- **0.9-1.0**: Multiple credible sources, verified
- **0.7-0.8**: Good evidence, some verification
- **0.5-0.6**: Reasonable evidence, limited verification
- **0.3-0.4**: Weak evidence
- **0.0-0.2**: Speculative or unverified

### Provenance Tracking

Every signal includes:
- Data collection method
- Processing steps with timestamps
- Complete source attribution
- Data quality assessment
- Verification status
- Formal citations

## Query Configuration

### Example Configurations

See `/queries/` directory:
- `example_psychology_research.json`
- `example_luxury_brands.json`
- `example_ai_regulation.json`

### Key Configuration Options

**Search Terms**: Keywords to search for
**Geographic Scope**: Regions to focus on
**Temporal Scope**: Time period to cover
**Data Sources**: Web search, publications, archive
**Signal Types**: Types to generate
**Confidence Threshold**: Minimum quality level
**Automation**: Schedule for repeated execution

## Best Practices

### For Best Results

✅ Use specific, domain-focused search terms
✅ Set appropriate confidence thresholds
✅ Review signals regularly
✅ Leverage provenance for verification
✅ Refine queries based on results

### Common Pitfalls to Avoid

❌ Too broad search terms
❌ Ignoring confidence scores
❌ Not checking provenance
❌ One-time queries for ongoing topics

## Integration with Manual Workflow

**Use Automated Queries When**:
- Researching broad topics
- Need latest data
- Want structured insights
- Require provenance

**Use Manual Fetching When**:
- Have specific URLs
- Monitoring specific subjects
- Prefer manual curation

**Combine Both**:
- Queries for discovery
- Manual fetch for specific articles
- Generate signals from either source

## Getting Help

- Signal schema: `/schemas/signal/signal-schema.json`
- Query schema: `/schemas/query/query-schema.json`
- Examples: `/queries/example_*.json`
- Ask Claude for help with any command

---

**Ready to start?** Try: `/query [your topic]`
