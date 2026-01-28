# Queries Directory

This directory contains query configurations that define automated research and signal generation operations.

## What are Query Configurations?

Query configurations are JSON files that specify:
- What topic to research
- How to search for information
- Where to look for data
- What types of signals to generate
- How to process and analyze results
- When to run automatically (if scheduled)

## Directory Contents

This directory contains saved query configurations:

- `example_psychology_research.json` - Psychology research monitoring
- `example_luxury_brands.json` - Luxury market intelligence  
- `example_ai_regulation.json` - AI regulation tracking

## File Naming Convention

**Format**: `query_[topic_name].json` or `example_[topic_name].json`

**Examples**:
- `query_psychology_research.json`
- `example_luxury_brands.json`

## Query Configuration Structure

Each query configuration conforms to `/schemas/query/query-schema.json` and includes:

### Core Information
- **query_id**: Unique identifier (e.g., `qry_20260128_psychology`)
- **query_name**: Human-readable name
- **query_type**: Type of query (broad_topic, specific_subject, trend_tracking, etc.)
- **topic**: Primary topic being researched

### Search Configuration
- **search_terms**: Keywords to search for
- **search_scope**: Geographic, temporal, and language parameters
- **data_sources**: Web search, publications, article archive

### Processing Instructions
- **signal_types**: Types of signals to generate (trend, insight, pattern, etc.)
- **min_confidence**: Minimum confidence threshold (0.0-1.0)
- **max_signals**: Maximum number of signals to generate
- **focus_areas**: Specific aspects to emphasize

### Automation Settings
- **enabled**: Whether automated execution is enabled
- **schedule**: When to run (daily, weekly, cron syntax)
- **auto_save_signals**: Automatically save generated signals
- **notification_enabled**: Send notifications on completion

### Filters & Quality
- **exclude_keywords**: Keywords to exclude from results
- **min_article_length**: Minimum article word count
- **source_credibility**: Credibility filter (any, verified_only, high_credibility)

### Provenance Configuration
- **track_all_sources**: Track all data sources in provenance
- **include_processing_steps**: Include detailed processing steps
- **citation_format**: Format for citations (APA, MLA, Chicago)

## Using Query Configurations

### Create New Query

Interactive creation:
```
/query-config create "your topic"
```

Manual creation:
1. Copy an example file from this directory
2. Modify the configuration
3. Save with new name
4. Run with `/query-config run [query_id]`

### List All Queries

```
/query-config list
```

### Run a Query

```
/query-config run qry_20260128_psychology
```

### Edit Existing Query

```
/query-config edit qry_20260128_psychology
```

## Example Query Configurations

### Example 1: Psychology Research

**File**: `example_psychology_research.json`

**Purpose**: Monitor psychology research and developments

**Configuration highlights**:
- Search terms: psychology research, studies, mental health, cognitive science
- Scope: Global, last 60 days
- Publications: Nature, Science, Psychology Today, APA
- Signal types: trend, insight, development
- Confidence threshold: 0.6

### Example 2: Luxury Market Intelligence

**File**: `example_luxury_brands.json`

**Purpose**: Track luxury market trends and consumer behavior

**Configuration highlights**:
- Search terms: luxury market, consumer behavior, brand strategy, retail
- Scope: Global (Europe, Asia, North America), last 30 days
- Publications: Financial Times, Business of Fashion, Vogue Business
- Signal types: trend, insight, opportunity
- Confidence threshold: 0.65
- Focus: consumer behavior, brand strategies, sustainability

### Example 3: AI Regulation Tracking

**File**: `example_ai_regulation.json`

**Purpose**: Monitor AI regulation and policy developments

**Configuration highlights**:
- Search terms: AI regulation, policy, governance, ethics, safety
- Scope: Global (US, EU, UK, China), last 45 days
- Publications: Politico, MIT Tech Review, FT, Economist
- Signal types: trend, development, risk, opportunity
- Confidence threshold: 0.7
- Focus: new regulations, enforcement, industry response
- Priority: Critical

## Query Types

### broad_topic
Research broad subjects like "psychology" or "luxury brands"
- Diverse search terms
- Wide information gathering
- Multiple perspectives

### specific_subject
Track specific entities like companies or people
- Focused search terms
- Coverage monitoring
- Mention tracking

### trend_tracking
Monitor evolving trends over time
- Temporal emphasis
- Velocity tracking
- Historical comparison

### competitive_intelligence
Competitive analysis and monitoring
- Multiple entity tracking
- Comparative analysis
- Market positioning

### custom
User-defined research objectives
- Flexible configuration
- Custom processing

## Automation

Queries can be scheduled to run automatically using the `schedule` field in `automation_config`:

**Daily**:
```json
"schedule": "daily"
```
Runs every day at 9 AM

**Weekly**:
```json
"schedule": "weekly"
```
Runs every Monday at 9 AM

**Custom (Cron Syntax)**:
```json
"schedule": "0 10 * * 2,5"
```
Runs Tuesdays and Fridays at 10 AM

The schedule field accepts:
- Simple string values: `"daily"`, `"weekly"`
- Standard cron syntax for custom schedules: `"MIN HOUR DAY MONTH WEEKDAY"`
- Examples: `"0 9 * * *"` (daily at 9 AM), `"0 9 * * 1"` (Mondays at 9 AM)

When automated:
- Query executes on schedule
- Signals generated and saved automatically
- Notifications sent if configured
- Execution history maintained

## Best Practices

### Search Terms
✅ Use specific, domain-focused keywords
✅ Include synonyms and variations
✅ Add industry-specific terminology
❌ Avoid generic, overly broad terms

### Scope
✅ Define appropriate time window
✅ Specify relevant geographic regions
✅ Set language preferences
❌ Don't make scope too narrow or too broad

### Signal Configuration
✅ Choose appropriate signal types
✅ Set realistic confidence thresholds
✅ Limit max signals to manageable number
✅ Define clear focus areas
❌ Don't generate low-confidence signals

### Automation
✅ Schedule based on topic velocity
✅ Enable notifications for critical queries
✅ Auto-save signals for convenience
❌ Don't over-automate low-priority topics

## Modifying Configurations

To modify an existing query:

1. **Via Command**:
   ```
   /query-config edit qry_20260128_psychology
   ```

2. **Manual Edit**:
   - Open the JSON file in this directory
   - Make changes while maintaining schema compliance
   - Save the file
   - Run with `/query-config run [query_id]`

3. **Validation**:
   - System validates against `/schemas/query/query-schema.json`
   - Reports any schema violations
   - Ensures all required fields present

## Query Execution Tracking

Each query configuration tracks:
- **created_date**: When query was created
- **created_by**: Who/what created it
- **last_executed**: Last execution timestamp
- **execution_count**: Number of times executed

This helps monitor query usage and effectiveness.

## Integration with Signal Generation

When a query executes:
1. System uses configuration to search for data
2. Fetches relevant articles
3. Passes to signal-generator with configuration parameters
4. Signals generated according to specifications
5. Complete provenance trail maintained
6. Results saved to `/signals/` directory

## Schema Reference

Full schema: `/schemas/query/query-schema.json`

Required fields:
- query_id
- query_name
- query_type
- topic
- search_terms
- created_date

Optional but recommended:
- search_scope
- data_sources
- processing_instructions
- automation_config
- provenance_config

## Getting Started

### Quick Start
Use an example as template:
```bash
# Copy example
cp example_psychology_research.json query_my_topic.json

# Edit with your parameters
# Run your query
/query-config run qry_[your_query_id]
```

### Interactive Creation
```bash
/query-config create "your topic"
```

### Simple Query
For one-time research without saving:
```bash
/query your topic
```

---

For detailed usage guide, see `/docs/QUERY_SYSTEM_GUIDE.md`
