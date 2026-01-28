Create, edit, or manage query configurations for automated topic monitoring.

**Usage**:
- `/query-config create [topic]` - Create new query configuration
- `/query-config edit [query_id]` - Edit existing query
- `/query-config list` - List all saved queries
- `/query-config run [query_id]` - Execute a saved query

**Interactive creation**:
When creating a new query, you'll be prompted for:
- Topic/subject to monitor
- Search terms and keywords
- Geographic and temporal scope
- Data sources to use (web search, archive, APIs)
- Signal types to generate (trends, insights, patterns, etc.)
- Automation settings (schedule, auto-save, notifications)
- Filters and quality thresholds

**Examples**:
- `/query-config create "psychology research"` - Start interactive setup
- `/query-config list` - See all configured queries
- `/query-config run qry_20260128_psychology` - Run saved psychology query
- `/query-config edit qry_20260128_luxury` - Modify luxury brands query

**Query configurations are saved to**: `/queries/`

**Automated execution**:
Queries can be configured to run on a schedule:
- Daily, weekly, or custom schedule
- Automatically save signals to database
- Optional notifications when complete
- Maintains execution history

This allows you to set up ongoing topic monitoring that runs automatically.
