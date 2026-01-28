# Signals Directory

This directory contains structured signals generated from media monitoring and topic research.

## What are Signals?

Signals are structured insights automatically extracted from articles and web data. Each signal represents a meaningful pattern, trend, or development identified by the system.

## Signal Types

- **Trend**: Directional movements or developments over time
- **Insight**: Non-obvious observations or understanding
- **Pattern**: Recurring themes or behaviors across sources
- **Anomaly**: Unexpected or unusual developments
- **Opportunity**: Potential areas for action or investigation
- **Risk**: Potential threats or challenges identified
- **Development**: New or emerging situations

## Directory Structure

```
/signals/
  /YYYY/                    # Year folders (e.g., 2026/)
    /MM_MonthName/          # Month folders (e.g., 01_Jan/)
      signal_*.json         # Signal data (machine-readable)
      signal_*.md           # Signal summaries (human-readable)
```

## File Naming Convention

**Format**: `signal_YYYYMMDD_HHMMSS_topic_name.json` or `.md`

**Example**: `signal_20260128_150943_ai_regulation.json`

Components:
- `signal_` - Static prefix
- `YYYYMMDD` - Date generated (year, month, day)
- `HHMMSS` - Time generated (hour, minute, second)
- `topic_name` - Brief topic description (lowercase, underscores)
- `.json` or `.md` - File format

## Signal Contents

### JSON File (.json)

Contains complete structured data conforming to `/schemas/signal/signal-schema.json`:

- **Identification**: Signal ID, type, topic, title
- **Content**: Summary, detailed analysis, implications
- **Scoring**: Confidence and relevance scores (0.0-1.0)
- **Sources**: All source articles with URLs and contribution descriptions
- **Context**: Temporal, geographic, and industry information
- **Provenance**: Complete data lineage with citations
- **Metadata**: Keywords, tags, priority

### Markdown File (.md)

Human-readable summary including:
- Signal title and type
- Summary (1-2 sentences)
- Detailed analysis
- Key implications
- Source list with links
- Confidence and relevance scores
- Provenance summary

## How Signals are Generated

### From Automated Queries

1. User executes query: `/query psychology`
2. System searches web and archive for relevant content
3. Fetches and processes articles
4. Analyzes data for patterns and trends
5. Generates signals with provenance tracking
6. Saves to this directory

### From Existing Archive

Signals can also be generated from articles already in the archive by using the query-orchestrator agent with archive-only data sources configured in the query configuration.

## Provenance & Quality

Every signal includes:

**Data Collection**:
- How data was gathered (web search, archive, API)
- Search queries used
- Sources accessed
- Retrieval timestamps

**Processing**:
- Steps taken to process data
- Agents involved
- Quality checks applied

**Source Attribution**:
- Complete list of source articles
- How each source contributed
- Additional data sources

**Quality Metrics**:
- Confidence score (0.0-1.0)
- Relevance score (0.0-1.0)
- Data quality assessment
- Verification status

## Using Signals

### View All Signals

```
/signals
```

### Filter by Topic

```
/signals --topic "psychology"
```

### Filter by Type

```
/signals --type trend
```

### View Recent Signals

```
/signals --recent 30
```

### View Specific Signal

```
/signals --id sig_20260128_150943_ai_regulation
```

### Export Signals

Signal data can be exported by reading the JSON files directly from the `/signals/` directory or by using standard file export tools.

## Integration

Signals can be:
- **Analyzed**: Use for research and decision-making
- **Exported**: Import into analytics platforms
- **Shared**: Distribute to stakeholders
- **Tracked**: Monitor changes over time
- **Aggregated**: Combine for higher-level insights

## Schema Compliance

All signals conform to `/schemas/signal/signal-schema.json`. This ensures:
- Consistent structure across all signals
- Validation of required fields
- Standardized provenance tracking
- Interoperability with downstream systems

## Best Practices

1. **Review Confidence Scores**: Higher confidence = stronger evidence
2. **Check Provenance**: Verify claims trace back to credible sources
3. **Consider Context**: Temporal and geographic scope matter
4. **Track Over Time**: Monitor how signals evolve
5. **Act Appropriately**: Use signals to inform decisions, not replace judgment

## Getting Started

Generate your first signals:

```
/query [your topic]
```

View results:

```
/signals
```

---

For detailed documentation, see `/docs/QUERY_SYSTEM_GUIDE.md`
