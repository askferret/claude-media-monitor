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

**Quality Metrics** (see [Quality Metrics & Methodology](#quality-metrics--methodology) below):
- Confidence score (0.0-1.0)
- Relevance score (0.0-1.0)
- Data quality assessment
- Verification status

## Quality Metrics & Methodology

How we assess and score each quality metric so you can interpret signals consistently.

### Confidence Score (0.0–1.0)

**What it measures**: How strongly the evidence supports the signal’s claim. Confidence reflects source strength, corroboration, and clarity of the pattern—not how important or interesting the signal is.

**Assessment**:
- **Source count & overlap**: Multiple independent sources that agree raise confidence; single-source or conflicting evidence lowers it.
- **Source credibility**: Established publications, research, or official data raise confidence; unknown or low-credibility sources lower it.
- **Evidence type**: Direct quotes, data, or named studies support higher scores; inference or interpretation without clear evidence supports lower scores.
- **Clarity of pattern**: A clear, specific pattern across sources supports higher confidence; vague or speculative patterns support lower confidence.

**Scoring bands** (used by the signal-generator):

| Band    | Score  | Meaning |
|---------|--------|--------|
| Strong  | 0.9–1.0 | Multiple high-credibility sources, clear evidence, verified facts |
| Good    | 0.7–0.8 | Good evidence from credible sources, some verification |
| Moderate| 0.5–0.6 | Reasonable evidence but limited sources or verification |
| Weak    | 0.3–0.4 | Weak evidence, single source, or questionable credibility |
| Low     | 0.0–0.2 | Speculative, unverified, or low-quality sources |

**Use**: Prefer higher-confidence signals for decisions; treat lower scores as hypotheses to validate.

### Relevance Score (0.0–1.0)

**What it measures**: How well the signal aligns with the query topic or monitoring objectives. Relevance is about fit to your research question, not strength of evidence.

**Assessment**:
- **Query alignment**: Does the signal directly address the query (e.g. “consumer culture and identity”) or only touch it indirectly?
- **Topic centrality**: Is this signal’s main theme the queried topic, or a side angle?
- **Actionability for scope**: Would acting on this signal clearly serve the stated monitoring or research goal?

**Scoring bands**:

| Band    | Score  | Meaning |
|---------|--------|--------|
| Direct  | 0.9–1.0 | Directly addresses the query topic, highly relevant |
| Strong  | 0.7–0.8 | Strongly related to query topic |
| Moderate| 0.5–0.6 | Moderately related, some relevance |
| Tangential | 0.3–0.4 | Tangentially related |
| Minimal | 0.0–0.2 | Minimal or unclear relevance |

**Use**: Filter or rank by relevance when you need signals tightly aligned to a specific topic or objective.

### Data Quality (provenance.data_quality_score, 0.0–1.0)

**What it measures**: Quality of the *underlying data* used to build the signal (sources and collection), not the quality of the analysis itself.

**Assessment**:
- **Source credibility & reputation**: Known, authoritative, or peer-reviewed sources raise the score.
- **Recency**: Data and articles that match the signal’s timeframe support higher scores; stale or mismatched dates lower it.
- **Completeness**: Sufficient articles and fields (dates, URLs, publications) support higher scores; missing metadata or thin coverage lower it.
- **Collection method**: Systematic collection (e.g. defined search + fetch) supports higher scores; ad hoc or unclear collection lowers it.

**Use**: When confidence and data quality diverge, treat data quality as the ceiling for how much to trust the evidence base.

### Verification Status (provenance.verification_status)

**What it measures**: Whether the signal’s claims have been checked against primary sources or other verification steps.

**Values**:

| Status             | Meaning |
|--------------------|--------|
| **verified**       | Key claims traced to primary sources or cross-checked; evidence clearly supports the summary. |
| **partially_verified** | Some claims linked to sources; others are inferred or not yet verified. |
| **unverified**     | Claims not yet traced to sources; based on analysis only. |

**Use**: Prefer verified (or partially_verified with clear caveats) when the signal will drive high-stakes decisions; treat unverified signals as prompts for further checking.

### How the metrics work together

- **Confidence** = strength of evidence for the signal.
- **Relevance** = fit to your query or monitoring goal.
- **Data quality** = quality of the raw inputs.
- **Verification** = whether claims have been checked.

Example: A signal can have high relevance (on-topic) but moderate confidence (limited sources). Another can have high confidence (strong evidence) but lower relevance (tangential to the query). Use all four to decide how much to rely on a signal and whether to validate it further.

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

1. **Review Confidence Scores**: Higher confidence = stronger evidence (see [Quality Metrics & Methodology](#quality-metrics--methodology))
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
