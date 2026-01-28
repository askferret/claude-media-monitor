Execute an automated query to research a broad topic, gather latest data through web searches, and generate structured signals with complete provenance tracking.

**Usage**: `/query [topic]` or `/query --config [query_config_file]`

**Examples**:
- `/query psychology` - Research psychology topic, generate insights
- `/query luxury brands` - Analyze luxury brand trends and developments  
- `/query artificial intelligence regulation` - Track AI policy developments
- `/query --config queries/ai_monitoring.json` - Execute saved query configuration

**What it does**:
1. Creates or loads query configuration for the topic
2. Executes automated web searches for latest relevant data
3. Fetches and saves articles from top results
4. Searches existing article archive for related content
5. Generates structured signals (trends, insights, patterns)
6. Maintains complete data provenance and citations
7. Saves signals to signal database
8. Produces comprehensive execution report

**Output**:
- New articles saved to `/articles/YYYY/MM_MonthName/`
- Signals saved to `/signals/YYYY/MM_MonthName/`
- Execution report in `/reports/`
- Query configuration saved to `/queries/` (for reuse)

This command eliminates manual article selection and automates the entire research-to-insight pipeline.
