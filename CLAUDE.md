# Claude Media Monitor - Automated Intelligence System

## Repository Purpose

This repository is an agent-native workspace for automated media intelligence and signal generation. It provides three core capabilities:

1. **Automated Topic Research**: Query broad topics with automated web searches, article retrieval, and insight generation
2. **Media Monitoring**: Track coverage about specific subjects across publications (manual or automated workflows)
3. **Signal Intelligence**: Transform raw data into structured insights with complete provenance tracking

## Key Innovation: Agent-Native Automation

Unlike traditional media monitoring systems that require manual article selection and processing, this system is designed for **complete automation**:

- **Query any topic** → System automatically searches, retrieves, analyzes, and generates insights
- **No manual selection** → Automated web searches find relevant content
- **Full provenance** → Every signal traces back to source data with complete citations
- **Structured outputs** → Signals conform to schemas for downstream processing
- **Database auto-population** → Signals and articles automatically saved and organized

## Directory Structure

```
/articles/              # All fetched articles organized by date
  /YYYY/               # Year folders (2000-2026+)
    /MM_MonthName/     # Month folders (01_Jan through 12_Dec)
      article_*.md     # Individual article files
/signals/              # Generated signals organized by date
  /YYYY/               # Year folders
    /MM_MonthName/     # Month folders
      signal_*.json    # Signal data (JSON format)
      signal_*.md      # Signal summaries (Markdown)
/queries/              # Query configurations for automation
  query_*.json         # Saved query configurations
/schemas/              # Data schemas and validation rules
  /fetched-article/    # Article schema and instructions
    fetch-schema.json       # JSON schema for article data
    fetch-instructions.md   # Detailed fetching guidelines
  /signal/             # Signal schema
    signal-schema.json      # JSON schema for signal data
  /query/              # Query configuration schema
    query-schema.json       # JSON schema for query configs
/.claude/              # Claude Code configuration
  /agents/             # Specialized subagents
  /commands/           # Slash commands for quick operations
/exports/              # Exported data files
/reports/              # Generated analysis reports
/publication-profiles/ # Publication metadata
```

## Article Organization System

### Storage Structure

**All articles MUST be saved in the `/articles/` directory following this hierarchy:**

1. **Year folder**: `/articles/YYYY/` (e.g., `/articles/2025/`)
2. **Month folder**: `/articles/YYYY/MM_MonthName/` (e.g., `/articles/2025/11_Nov/`)
3. **Article file**: Individual markdown files with structured naming

### File Naming Convention

**Format**: `article_theme_DDMMYY_publication.md`

**Components**:
- `article_` - Static prefix for all files
- `theme` - 2-4 keyword description of the article topic (lowercase, underscores between words)
- `DDMMYY` - Publication date (day, month, year in 2 digits each)
- `publication` - Abbreviated publication name (lowercase, simplified)

**Examples**:
- `article_climate_policy_debate_171025_economist.md`
- `article_ai_regulation_europe_030325_ft.md`
- `article_tech_industry_layoffs_280624_nytimes.md`

### Content Structure

Each article file must include:

1. **Metadata Header** (YAML front matter or markdown section):
   - Article title
   - Publication name
   - Publication date
   - Article URL
   - Date fetched
   - Author(s)
   - Keywords/tags

2. **Article Content**:
   - Clean markdown formatting
   - Preserved structure (headings, paragraphs, lists)
   - No advertisements or navigation elements
   - Proper markdown syntax throughout

## JSON Schema Compliance

All fetched articles must conform to the schema defined in `/schemas/fetched-article/fetch-schema.json`.

**Required fields include**:
- title, pub_name, article_url
- full_text, article_word_count
- claude_summary
- is_coverage, is_oped, by_subject
- has_comments
- keywords (array of 5 tags)
- display_summary

**Optional enrichment fields**:
- Author information (name, title, bio)
- Publication details (summary, editorial leaning)
- Comment analysis (summary, sentiment score, count)

See `/schemas/fetched-article/fetch-instructions.md` for detailed fetching guidelines.

## Automated Query System (New!)

### Overview

The automated query system enables **agent-native, streamlined automation** for topic research and signal generation. This eliminates manual article selection and automates the entire pipeline from query to insights.

### Native Query Capabilities

**Broad Topic Searches**:
- Query any broad topic: "psychology", "luxury brands", "artificial intelligence"
- System automatically generates optimal search terms
- Executes web searches for latest data
- Retrieves and processes relevant articles
- Generates structured insights automatically

**Automated Web Search**:
- Real-time web searches for current information
- Prioritizes credible, recent sources
- Filters by relevance, date, and quality
- Tracks all search queries for provenance

**Signal Generation**:
- Processes data into structured signals
- Types: trends, insights, patterns, anomalies, opportunities, risks, developments
- Each signal includes confidence and relevance scores
- Complete source attribution and citations

**Data Provenance**:
- Full tracking of data collection methods
- Complete processing history
- All sources cited in standard format
- Verification status for each signal
- Quality scores for underlying data

### Signal Database

**Automated Population**:
- Signals automatically saved to `/signals/` directory
- Organized by date (YYYY/MM_MonthName/)
- Both JSON (data) and Markdown (readable) formats
- Searchable by topic, type, date, confidence

**Signal Schema**:
Signals conform to `/schemas/signal/signal-schema.json`:
- **Identification**: Signal ID, type, topic, title
- **Content**: Summary, detailed analysis, implications
- **Scoring**: Confidence (0.0-1.0), relevance (0.0-1.0)
- **Sources**: Complete list of source articles and data
- **Context**: Temporal, geographic, industry information
- **Provenance**: Collection method, processing steps, quality assessment, citations
- **Metadata**: Keywords, related topics, priority, visibility

### Query Configuration

**Defining Queries**:
Queries can be created and saved for repeated execution:
- Query ID, name, and type
- Search terms and scope parameters
- Data source configuration
- Processing instructions (signal types, thresholds, focus areas)
- Automation settings (schedule, auto-save, notifications)

**Query Types**:
- `broad_topic`: Research broad subjects (psychology, luxury)
- `specific_subject`: Track specific entities or subjects
- `trend_tracking`: Monitor evolving trends over time
- `competitive_intelligence`: Competitive analysis and monitoring
- `custom`: User-defined research objectives

**Automation**:
- Schedule queries to run automatically (daily, weekly, custom)
- Signals auto-saved to database
- Optional notifications on completion
- Maintains execution history and statistics

### Workflow: Automated Topic Research

**Example: Psychology Research**

```
1. User: "/query psychology"

2. System:
   a. Creates query configuration
   b. Generates search terms: "psychology research", "psychological studies", 
      "mental health developments", "cognitive science"
   c. Executes web searches
   d. Identifies top 15-20 relevant articles from past 60 days
   e. Fetches full article content
   f. Saves articles to /articles/YYYY/MM_MonthName/
   g. Searches existing archive for related content
   h. Compiles all sources for analysis

3. Signal Generation:
   a. Analyzes all collected data
   b. Identifies patterns, trends, developments
   c. Generates 5-8 signals with confidence scores
   d. Builds complete provenance trail
   e. Creates formal citations for all sources
   f. Saves signals to /signals/YYYY/MM_MonthName/

4. Output:
   - Execution report with summary statistics
   - All signals available via /signals command
   - New articles integrated into archive
   - Query configuration saved for reuse
```

**No manual intervention required** - from topic to actionable insights automatically.

### Provenance Tracking

Every signal maintains complete data lineage:

**Data Collection**:
- How data was collected (web search, API, archive)
- Search queries used
- Sources accessed and selection criteria
- Retrieval timestamps

**Processing Steps**:
- Each transformation step documented
- Agents/systems involved
- Timestamps for each step
- Quality checks applied

**Source Attribution**:
- Every claim traceable to specific source
- Article URLs, publications, dates
- How each source contributed to the signal
- Additional data sources beyond articles

**Quality & Verification**:
- Data quality scores
- Source credibility assessment
- Verification status (verified/partially_verified/unverified)
- Citations in standard format (APA, MLA, Chicago)

### Query Execution vs. Manual Fetching

**Use Automated Queries When**:
- Researching a broad topic
- Need latest/current data
- Want multiple perspectives
- Require structured insights
- Need complete provenance

**Use Manual Fetching When**:
- Have specific article URLs
- Monitoring specific subjects
- Building focused collection
- Manual curation preferred

## Workflow Overview

### Standard Article Capture Workflow

1. **Receive URL**: User provides article URL to fetch
2. **Invoke Agent**: Use the `article-fetcher` agent or `/fetch` command
3. **Extraction**: Agent fetches content and extracts metadata
4. **Schema Validation**: Content structured according to JSON schema
5. **Organization**: File saved to appropriate date-based folder
6. **Confirmation**: Location and filename reported back

### Batch Processing Workflow

For multiple articles:
1. User provides list of URLs or search criteria
2. Use `batch-fetch` agent to process multiple articles
3. Each article follows standard workflow
4. Summary report generated at completion

## Available Tools

### Subagents

Located in `.claude/agents/`:

1. **query-orchestrator**: **[NEW]** Orchestrate automated topic research and signal generation
   - Execute comprehensive queries on broad topics
   - Coordinate web searches, article retrieval, and processing
   - Manage data flow from raw data to structured signals
   - Ensure complete provenance tracking
   - Generate execution reports

2. **signal-generator**: **[NEW]** Generate structured insights from articles and data
   - Analyze multiple sources to identify patterns and trends
   - Create structured signals (trends, insights, patterns, etc.)
   - Assign confidence and relevance scores
   - Build complete provenance trails with citations
   - Output JSON and Markdown formats

3. **article-fetcher**: Primary agent for fetching and saving individual articles
   - Handles complete fetch-to-save workflow
   - Extracts metadata and formats content
   - Ensures schema compliance
   - Organizes by date

4. **batch-fetch**: Process multiple articles in one operation
   - Accepts list of URLs
   - Processes each article systematically
   - Provides progress updates
   - Generates batch summary report

5. **article-analyzer**: Analyze existing articles in the repository
   - Generate statistics and insights
   - Identify trends across articles
   - Create summary reports
   - Export data in various formats

6. **publication-profiler**: Research and profile publications
   - Gather publication metadata
   - Assess editorial bias/leaning
   - Track publication patterns
   - Maintain publication database

7. **archive-organizer**: Maintain and optimize the article archive
   - Validate file naming consistency
   - Check schema compliance
   - Identify duplicates
   - Generate archive reports

### Slash Commands

Located in `.claude/commands/`:

1. **/query**: **[NEW]** Execute automated topic research with signal generation
2. **/signals**: **[NEW]** View and search signal database
3. **/query-config**: **[NEW]** Create and manage query configurations
4. **/fetch**: Quick article fetch - provide URL, get article saved
5. **/batch**: Batch process multiple URLs at once
6. **/analyze**: Analyze the article archive and generate reports
7. **/validate**: Validate existing articles against schema
8. **/stats**: Show statistics about the article collection
9. **/search**: Search articles by keyword, publication, or date
10. **/export**: Export articles in various formats (CSV, JSON, etc.)
11. **/profile-pub**: Profile a publication for metadata enrichment

## Quality Standards

### Content Quality
- Remove all advertisements, navigation, and non-article elements
- Preserve article formatting (bold, italics, lists, quotes)
- Maintain paragraph breaks and section structure
- Include image alt-text descriptions where relevant
- Ensure proper markdown syntax

### Metadata Quality
- Accurate publication identification
- Correct date extraction (or current date if unavailable)
- Descriptive theme keywords (2-4 words)
- Complete author information when available
- Proper classification (coverage/op-ed/by-subject)

### Organizational Quality
- Consistent file naming across all articles
- Proper date-based folder structure
- No orphaned files outside the structure
- Regular validation against schema

## Error Handling

**Common scenarios**:

1. **Paywall articles**: Inform user, suggest alternatives or manual intervention
2. **Invalid URLs**: Report issue clearly, request valid URL
3. **Missing publication name**: Use "unknown" as publication identifier
4. **Missing publication date**: Use current date (fetch date)
5. **Ambiguous theme**: Request 2-4 keywords from user
6. **Schema validation failures**: Report specific issues, fix and retry

## Usage Guidelines

### When Working with Articles

1. **Always use the date-based structure** - Never save articles to repository root
2. **Follow naming conventions exactly** - Consistency is critical for searchability
3. **Validate against schema** - Ensure all required fields are populated
4. **Preserve content quality** - Clean extraction with proper formatting
5. **Document fetch context** - Note date fetched, any issues encountered

### When Adding Features

1. **Respect existing structure** - Don't reorganize the archive without explicit approval
2. **Maintain schema compatibility** - Changes should be backward compatible
3. **Update documentation** - Keep this CLAUDE.md synchronized with functionality
4. **Test thoroughly** - Validate with sample articles before batch processing

### Performance Optimization

1. **Batch operations** - Use batch agent for multiple articles
2. **Parallel processing** - Process independent articles concurrently where possible
3. **Cache publication metadata** - Avoid redundant lookups
4. **Index for search** - Maintain search indices for large collections

## Integration Points

### With MCP Servers

This repository can integrate with:
- **Context7**: For API documentation when building analysis tools
- **Resend**: For email notifications about new articles or reports
- **Time**: For accurate date/time stamping

### With External Tools

- **Notion**: Export summaries and reports to Notion workspace
- **Obsidian**: Can reference articles in Daniel's reference notes
- **Analytics platforms**: Export data for visualization and analysis

## Monitoring Subject Context

If this repository is used for media monitoring about a specific subject:

1. Check this CLAUDE.md for subject identification
2. Subject context informs the `by_subject` field in article schema
3. Adjust analysis and tagging based on subject relevance
4. Track sentiment and coverage patterns related to subject

**Current Subject**: [Define subject here if applicable, e.g., "Daniel Rosehill", "DSR Holdings", or "general research collection"]

## Maintenance Tasks

### Regular Maintenance
- Validate file naming consistency across archive
- Check for schema compliance issues
- Remove duplicate articles
- Update publication profiles
- Generate periodic statistics reports

### Data Quality Audits
- Review article summaries for accuracy
- Validate keyword relevance
- Check metadata completeness
- Assess classification accuracy (coverage/op-ed/by-subject)

## Best Practices

1. **Be Systematic**: Follow the established structure and workflows
2. **Validate Early**: Check schema compliance during fetch, not after
3. **Document Thoroughly**: Complete all metadata fields comprehensively
4. **Stay Organized**: Use date-based structure consistently
5. **Quality Over Quantity**: Ensure clean, accurate extractions
6. **Automate When Possible**: Use batch operations and automation tools
7. **Version Control**: Commit logical groups of articles with clear messages

## Getting Started

**To fetch your first article**:
```
User: "Fetch this article: [URL]"
Claude: [Invokes article-fetcher agent, processes, saves to correct location]
```

**To fetch multiple articles**:
```
User: "Fetch these articles: [URL1], [URL2], [URL3]"
Claude: [Invokes batch-fetch agent, processes all, provides summary]
```

**To analyze your collection**:
```
User: "/analyze"
Claude: [Generates statistics and insights report]
```

---

This system is designed to make media monitoring and research data collection systematic, searchable, and maintainable over time. Follow these guidelines consistently to build a valuable article archive.
