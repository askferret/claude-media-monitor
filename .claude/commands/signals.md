View, search, and analyze signals in the signal database.

**Usage**: 
- `/signals` - List all signals
- `/signals --topic [topic]` - Filter by topic
- `/signals --type [type]` - Filter by signal type (trend/insight/pattern/etc.)
- `/signals --recent [days]` - Show signals from last N days
- `/signals --id [signal_id]` - View specific signal details

**Examples**:
- `/signals` - Show all signals with summary
- `/signals --topic "artificial intelligence"` - Show AI-related signals
- `/signals --type trend --recent 30` - Recent trend signals
- `/signals --id sig_20260128_150943_ai_regulation` - View specific signal

**What it displays**:
- Signal title, type, and topic
- Confidence and relevance scores
- Summary and key implications
- Source article count
- Generation date
- Full provenance trail (if viewing specific signal)

**Output formats available**:
- Table view (default)
- Detailed view (for specific signal)
- JSON export (add `--json`)
- CSV export (add `--csv`)

Signals are structured insights generated from articles and web data with complete citation trails.
