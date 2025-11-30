<p align="center">
   <img src="assets/Council_of_HAL__Multi-LLM_Deliberation_Engine.png" alt="Council-Of-HALs Logo" width="400">
</p>

# Council-Of-HALs

*Kinda like the Council of Ricks, but make it AI, bringing your own deliberation council straight into your assistant/IDE/CLI of choice!*

An MCP server that orchestrates true deliberative consensus - imagine HAL 9000, Jarvis, and Skynet sitting down for a civilized chat about your next big decision. Models actually debate each other across multiple rounds, refining their positions like philosophers in a cosmic symposium.

![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)
![Python 3.11+](https://img.shields.io/badge/python-3.11+-blue.svg)
![Platform](https://img.shields.io/badge/platform-macOS%20%7C%20Linux%20%7C%20Windows-lightgrey.svg)
![MCP](https://img.shields.io/badge/MCP-Server-green.svg)
![Code style: black](https://img.shields.io/badge/code%20style-black-000000.svg)

## 🎬 See It In Action

**Cloud Models Debate** (Claude Sonnet, GPT-5.1 Codex, Gemini):
```javascript
mcp__council-of-hals__deliberate({
  question: "Should we use REST or GraphQL for our new API?",
  participants: [
    {cli: "claude", model: "claude-sonnet-4-5-20250929"},
    {cli: "codex", model: "gpt-5.1-codex"},
    {cli: "gemini", model: "gemini-2.5-pro"}
  ],
  mode: "conference",
  rounds: 3
})
```
**Result**: Converged on hybrid architecture (0.82-0.95 confidence) • [View full transcript](transcripts/20251030_153509_Should_we_use_REST_or_GraphQL_for_our_new_API_Con.md)

**Local Models Debate** (100% private, zero API costs):
```javascript
mcp__council-of-hals__deliberate({
  question: "Should we prioritize code quality or delivery speed?",
  participants: [
    {cli: "ollama", model: "llama3.1:8b"},
    {cli: "ollama", model: "mistral:7b"},
    {cli: "ollama", model: "deepseek-r1:8b"}
  ],
  mode: "conference",
  rounds: 2
})
```
**Result**: 2 models switched positions after Round 1 debate • [View full transcript](transcripts/20251030_153834_Should_we_prioritize_code_quality_or_delivery_spee.md)

---

## What Makes This Different

**Council-Of-HALs enables TRUE deliberative consensus** - not just parallel opinions, but actual back-and-forth debate where models see each other's responses and evolve their thinking like a digital UN Security Council meeting:

- 🤝 **Real Debate**: Models actually converse and respond to each other (no more lonely monologues)
- 🔄 **Multi-Round Evolution**: Positions refine across rounds like a philosophical symposium
- 🗳️ **Structured Voting**: Models cast votes with confidence levels and rationale
- 📜 **Complete Audit Trail**: AI-generated summaries of every cosmic conversation
- ⚡ **Smart Early Stopping**: Automatically wraps up when consensus hits (saves those precious API credits)

## Features

- 🎯 **Two Debate Modes**: `quick` (swift verdict) or `conference` (epic multi-round symposium)
- 🤖 **Cosmic Model Mix**: CLI titans (claude, codex, droid, gemini) + HTTP guardians (ollama, lmstudio, openrouter)
- ⚡ **Auto-Convergence**: Smart shutdown when opinions align (preserves your API wallet)
- 🗳️ **Structured Voting**: Models cast votes with confidence scores and battle rationale
- 🧮 **Semantic Sorcery**: Similar options magically merge (0.70+ similarity threshold)
- 🎛️ **Model Mutiny Control**: AIs decide when the debate party ends
- 🔬 **Evidence Expedition**: Models can hack your codebase - read files, grep code, list dirs, run safe commands
- 💰 **Local Model Sanctuary**: Zero-cost deliberations with Ollama, LM Studio, llamacpp
- 🔐 **Data Fortress**: Keep everything on-prem with self-hosted models (no cloud spies)
- 🧠 **Memory Matrix**: Learns from past deliberations, injects context for warp-speed convergence
- 🔍 **Semantic Oracle**: Query decision history (find contradictions, trace evolution, spot patterns)
- 🛡️ **Fault Fortress**: One model crashes? The council carries on undeterred
- 📝 **Transcript Time Machine**: Full markdown chronicles with AI-generated plot summaries

## Quick Start

Ready to assemble your AI council? Let's get these digital deities debating in minutes:

1. **Summon the Dependencies** – Follow the [Installation](#installation) ritual to create your virtual environment and install the sacred packages.
2. **Configure the Council** – Set up your MCP client with the `.mcp.json` template in [Configure in Claude Code](#configure-in-claude-code).
3. **Ignite the Server** – Fire up `python server.py` and unleash the `deliberate` tool with the examples in [Usage](#usage).

**Try a Deliberation:**

```javascript
// Mix local + cloud models, zero API costs for local models
mcp__council-of-hals__deliberate({
  question: "Should we add unit tests to new features?",
  participants: [
    {cli: "ollama", model: "llama2"},           // Local
    {cli: "lmstudio", model: "mistral"},        // Local
    {cli: "claude", model: "sonnet"}            // Cloud
  ],
  mode: "quick"
})
```

> **⚠️ Model Size Matters for Deliberations**
>
> **Recommended**: Use 7B-8B+ parameter models (Llama-3-8B, Mistral-7B, Qwen-2.5-7B) for reliable structured output and vote formatting.
>
> **Not Recommended**: Models under 3B parameters (e.g., Llama-3.2-1B) may struggle with complex instructions and produce invalid votes.

**Available Models**: `claude` (opus 4.5, sonnet, haiku), `codex` (gpt-5.1-codex), `droid`, `gemini`, HTTP adapters (ollama, lmstudio, openrouter).
See [CLI Model Reference](docs/CLI_MODEL_REFERENCE.md) for complete details.

> **🧠 Reasoning Effort Control**
>
> Control reasoning depth per-participant for codex and droid adapters:
> ```javascript
> participants: [
>   {cli: "codex", model: "gpt-5.1-codex", reasoning_effort: "high"},    // Deep reasoning
>   {cli: "droid", model: "gpt-5.1-codex", reasoning_effort: "low"}      // Fast response
> ]
> ```
> - **Codex**: `none`, `minimal`, `low`, `medium`, `high`, `xhigh`
> - **Droid**: `off`, `low`, `medium`, `high`
> - Config defaults set in `config.yaml`, per-participant overrides at runtime

For model choices and picker workflow, see [Model Registry & Picker](docs/model-registry-and-picker.md).

## Installation

### Prerequisites

1. **Python 3.11+**: `python3 --version`
2. **At least one AI tool** (optional - HTTP adapters work without CLI):
   - **Claude CLI**: https://docs.claude.com/en/docs/claude-code/setup
   - **Codex CLI**: https://github.com/openai/codex
   - **Droid CLI**: https://github.com/Factory-AI/factory
   - **Gemini CLI**: https://github.com/google-gemini/gemini-cli

### Setup

```bash
python3 -m venv .venv
source .venv/bin/activate  # macOS/Linux; Windows: .venv\Scripts\activate
pip install -r requirements.txt
python3 -m pytest tests/unit -v  # Verify installation
```

✅ Ready to use! Server includes core dependencies plus optional convergence backends (scikit-learn, sentence-transformers) for best accuracy.

## Configuration

Edit `config.yaml` to configure adapters and settings:

```yaml
adapters:
  claude:
    type: cli
    command: "claude"
    args: ["-p", "--model", "{model}", "--settings", "{\"disableAllHooks\": true}", "{prompt}"]
    timeout: 300

  ollama:
    type: http
    base_url: "http://localhost:11434"
    timeout: 120
    max_retries: 3

defaults:
  mode: "quick"
  rounds: 2
  max_rounds: 5
```

**Note:** Use `type: cli` for CLI tools and `type: http` for HTTP adapters (Ollama, LM Studio, OpenRouter).

### Model Registry Configuration

Control which models are available for selection in the model registry. Each model can be enabled or disabled without removing its definition:

```yaml
model_registry:
  claude:
    - id: "claude-sonnet-4-5-20250929"
      label: "Claude Sonnet 4.5"
      tier: "balanced"
      default: true
      enabled: true  # Model is active and available
    - id: "claude-opus-4-20250514"
      label: "Claude Opus 4"
      tier: "premium"
      enabled: false  # Temporarily disabled (cost control, testing, etc.)
```

**Enabled Field Behavior:**
- `enabled: true` (default) - Model appears in `list_models` and can be selected for deliberations
- `enabled: false` - Model is hidden from selection but definition retained for easy re-enabling
- Disabled models cannot be used even if explicitly specified in `deliberate` calls
- Default model selection skips disabled models automatically

**Use Cases:**
- **Cost Control**: Disable expensive models temporarily without losing configuration
- **Testing**: Enable/disable specific models during integration tests
- **Staged Rollout**: Configure new models as disabled, enable when ready
- **Performance Tuning**: Disable slow models during rapid iteration
- **Compliance**: Temporarily restrict models pending approval

## Core Features Deep Dive

### Convergence Detection & Auto-Stop
Models automatically converge and stop deliberating when opinions stabilize, saving time and API costs. Status: Converged (≥85% similarity), Refining (40-85%), Diverging (<40%), or Impasse (stable disagreement). Voting takes precedence: when models cast votes, convergence reflects voting outcome.

→ **[Complete Guide](docs/convergence-detection.md)** - Thresholds, backends, configuration

### Structured Voting
Models cast votes with confidence levels (0.0-1.0), rationale, and continue_debate signals. Votes determine consensus: Unanimous (3-0), Majority (2-1), or Tie. Similar options automatically merged at 0.70+ similarity threshold.

→ **[Complete Guide](docs/structured-voting.md)** - Vote structure, examples, integration

### HTTP Adapters & Local Models
Run Ollama, LM Studio, or OpenRouter locally for zero API costs and complete data privacy. Mix with cloud models (Claude, GPT-4) in single deliberation.

→ **[Setup Guides](docs/http-adapters/intro.md)** - Ollama, LM Studio, OpenRouter, cost analysis

### Extending Council-Of-HALs
Add new CLI tools or HTTP adapters to fit your infrastructure. Simple 3-5 step process with examples and testing patterns.

→ **[Developer Guide](docs/adding-adapters.md)** - Step-by-step tutorials, real-world examples

## Evidence-Based Deliberation

Ground design decisions in reality by querying actual code, files, and data:

```javascript
// MCP client example (e.g., Claude Code)
mcp__council_of_hals__deliberate({
  question: "Should we migrate from SQLite to PostgreSQL?",
  participants: [
    {cli: "claude", model: "sonnet"},
    {cli: "codex", model: "gpt-4"}
  ],
  rounds: 3,
  working_directory: process.cwd()  // Required - enables tools to access your files
})
```

**During deliberation, models can:**
- 📄 Read files: `TOOL_REQUEST: {"name": "read_file", "arguments": {"path": "config.yaml"}}`
- 🔍 Search code: `TOOL_REQUEST: {"name": "search_code", "arguments": {"pattern": "database.*connect"}}`
- 📋 List files: `TOOL_REQUEST: {"name": "list_files", "arguments": {"pattern": "*.sql"}}`
- ⚙️ Run commands: `TOOL_REQUEST: {"name": "run_command", "arguments": {"command": "git", "args": ["log", "--oneline"]}}`

**Example workflow:**
1. Model A proposes PostgreSQL based on assumptions
2. Model B requests: `read_file` to check current config
3. Tool returns: `database: sqlite, max_connections: 10`
4. Model B searches: `search_code` for database queries
5. Tool returns: 50+ queries with complex JOINs
6. Models converge: "PostgreSQL needed for query complexity and scale"
7. Decision backed by evidence, not opinion

**Benefits:**
- Decisions rooted in current state, not assumptions
- Applies to code reviews, architecture choices, testing strategy
- Full audit trail of evidence in transcripts

**Supported Tools:**
- `read_file` - Read file contents (max 1MB)
- `search_code` - Search regex patterns (ripgrep or Python fallback)
- `list_files` - List files matching glob patterns
- `run_command` - Execute safe read-only commands (ls, git, grep, etc.)

### Configuration

Control tool behavior in `config.yaml`:

**Working Directory** (Required):
- Set `working_directory` parameter when calling `deliberate` tool
- Tools resolve relative paths from this directory
- Example: `working_directory: process.cwd()` in JavaScript MCP clients

**Tool Security** (`deliberation.tool_security`):
- `exclude_patterns`: Block access to sensitive directories (default: `transcripts/`, `.git/`, `node_modules/`)
- `max_file_size_bytes`: File size limit for `read_file` (default: 1MB)
- `command_whitelist`: Safe commands for `run_command` (ls, grep, find, cat, head, tail)

**File Tree** (`deliberation.file_tree`):
- `enabled`: Inject repository structure into Round 1 prompts (default: true)
- `max_depth`: Directory depth limit (default: 3)
- `max_files`: Maximum files to include (default: 100)

**Adapter-Specific Requirements:**

| Adapter | Working Directory Behavior | Configuration |
|---------|---------------------------|---------------|
| **Claude** | Automatic isolation via subprocess `{working_directory}` | No special config needed |
| **Codex** | No true isolation - can access any file | Security consideration: models can read outside `{working_directory}` |
| **Droid** | Automatic isolation via subprocess `{working_directory}` | No special config needed |
| **Gemini** | Enforces workspace boundaries | **Required**: `--include-directories {working_directory}` flag |
| **Ollama/LMStudio** | N/A - HTTP adapters | No file system access restrictions |

**Learn More:**
- [Complete Configuration Reference](CLAUDE.md#configuration-notes) - All config.yaml settings explained
- [Working Directory Isolation](CLAUDE.md#core-components) - How adapters handle file paths
- [Tool Security Model](CLAUDE.md#evidence-based-deliberation) - Whitelists, limits, and exclusions
- [Adding Custom Tools](docs/adding-tool.md) - Developer guide for extending the tool system

### Troubleshooting

**"File not found" errors:**
- Ensure `working_directory` is set correctly in your MCP client call
- Use discovery pattern: `list_files` → `read_file`
- Check file paths are relative to working directory

**"Access denied: Path matches exclusion pattern":**
- Tools block `transcripts/`, `.git/`, `node_modules/` by default
- Customize via `deliberation.tool_security.exclude_patterns` in config.yaml

**Gemini "File path must be within workspace" errors:**
- Verify Gemini's `--include-directories` flag uses `{working_directory}` placeholder
- See adapter-specific setup above

**Tool timeout errors:**
- Increase `deliberation.tool_security.tool_timeout` for slow operations
- Default: 10 seconds for file operations, 30 seconds for commands

**Learn More:**
- [Adding Custom Tools](docs/adding-tool.md) - Developer guide for extending tool system
- [Architecture & Security](CLAUDE.md#evidence-based-deliberation) - How tools work under the hood
- [Common Gotchas](CLAUDE.md#common-gotchas) - Advanced settings and known issues

## Decision Graph Memory

**The Council's Neural Network** - Council-Of-HALs evolves with each deliberation, building a collective consciousness that accelerates future decisions. Two core superpowers:

### 1. Automatic Context Injection
When starting a new deliberation, the system:
- Searches past debates for similar questions (semantic similarity)
- Finds the top-k most relevant decisions (configurable, default: 3)
- Injects context into Round 1 prompts automatically
- Result: Models start with institutional knowledge, converge faster

### 2. Semantic Search with `query_decisions`
Query past deliberations programmatically:
- **Search similar**: Find decisions related to a question
- **Find contradictions**: Detect conflicting past decisions
- **Trace evolution**: See how opinions changed over time
- **Analyze patterns**: Identify recurring themes

**Configuration** (optional - defaults work out-of-box):
```yaml
decision_graph:
  enabled: true                       # Auto-injection on by default
  db_path: "decision_graph.db"        # Resolves to project root (works for any user/folder)
  similarity_threshold: 0.6           # Adjust to control context relevance
  max_context_decisions: 3            # How many past decisions to inject
```

**Works for any user from any directory** - database path is resolved relative to project root.

→ **[Quickstart](docs/decision-graph/quickstart.md)** | **[Configuration](docs/decision-graph/configuration.md)** | **[Context Injection](docs/decision-graph/using-context-injection.md)**

## Usage

### Start the Server

```bash
python server.py
```

### Configure in Claude Code

**Option A: Project Config (Recommended)** - Create `.mcp.json`:

```json
{
  "mcpServers": {
    "council-of-hals": {
      "type": "stdio",
      "command": ".venv/bin/python",
      "args": ["server.py"],
      "env": {}
    }
  }
}
```

**Option B: User Config** - Add to `~/.claude.json` with absolute paths.

After configuration, restart Claude Code.

### Model Selection & Session Defaults

- Discover the allowlisted models for each adapter by running the MCP tool `list_models`.
- Set per-session defaults with `set_session_models`; leave `model` blank in `deliberate` to use those defaults.
- Full instructions and request examples live in [Model Registry & Picker](docs/model-registry-and-picker.md).

### Examples

**Quick Mode:**
```javascript
mcp__council-of-hals__deliberate({
  question: "Should we migrate to TypeScript?",
  participants: [{cli: "claude", model: "sonnet"}, {cli: "codex", model: "gpt-5.1-codex"}],
  mode: "quick"
})
```

**Conference Mode (multi-round):**
```javascript
mcp__council-of-hals__deliberate({
  question: "JWT vs session-based auth?",
  participants: [
    {cli: "claude", model: "sonnet"},
    {cli: "codex", model: "gpt-5.1-codex"}
  ],
  rounds: 3,
  mode: "conference"
})
```

**Search Past Decisions:**
```javascript
mcp__council-of-hals__query_decisions({
  query_text: "database choice",
  threshold: 0.5,  // NEW! Adjust sensitivity (0.0-1.0, default 0.6)
  limit: 5
})
// Returns: Similar past deliberations with consensus and similarity scores

// NEW! Empty results include helpful diagnostics:
{
  "type": "similar_decisions",
  "count": 0,
  "results": [],
  "diagnostics": {
    "total_decisions": 125,
    "best_match_score": 0.45,
    "near_misses": [{"question": "Database indexing...", "score": 0.45}],
    "suggested_threshold": 0.45,
    "message": "No results found above threshold 0.6. Best match scored 0.450. Try threshold=0.45..."
  }
}

// Find contradictions
mcp__council-of-hals__query_decisions({
  operation: "find_contradictions"
})
// Returns: Decisions where consensus conflicts

// Trace evolution
mcp__council-of-hals__query_decisions({
  query: "microservices architecture",
  operation: "trace_evolution"
})
// Returns: How opinions evolved over time on this topic
```

### Transcripts

All deliberations saved to `transcripts/` with AI-generated summaries and full debate history.

## Architecture

```
council-of-hals/
├── server.py                # MCP server entry point
├── config.yaml              # Configuration
├── adapters/                # CLI/HTTP adapters
│   ├── base.py             # Abstract base
│   ├── base_http.py        # HTTP base
│   └── [adapter implementations]
├── deliberation/            # Core engine
│   ├── engine.py           # Orchestration
│   ├── convergence.py      # Similarity detection
│   └── transcript.py       # Markdown generation
├── models/                  # Data models (Pydantic)
├── tests/                   # Unit/integration/e2e tests
└── decision_graph/         # Optional memory system
```

## Documentation Hub

### Getting Started
- **[Quick Start](README.md#quick-start)** - 5-minute setup
- **[Installation](README.md#installation)** - Detailed prerequisites and setup
- **[Usage Examples](README.md#usage)** - Quick and conference modes

### Core Concepts
- **[Convergence Detection](docs/convergence-detection.md)** - Auto-stop, thresholds, backends
- **[Structured Voting](docs/structured-voting.md)** - Vote structure, consensus types, vote grouping
- **[Evidence-Based Deliberation](README.md#evidence-based-deliberation)** - Ground decisions in reality with read_file, search_code, list_files, run_command
- **[Decision Graph Memory](docs/decision-graph/quickstart.md)** - Learning from past decisions

### Setup & Configuration
- **[HTTP Adapters](docs/http-adapters/intro.md)** - Ollama, LM Studio, OpenRouter setup
- **[Configuration Reference](docs/convergence-detection.md#configuration)** - All YAML options
- **[Migration Guide](docs/migration/cli_tools_to_adapters.md)** - From cli_tools to adapters

### Development
- **[Adding Adapters](docs/adding-adapters.md)** - CLI and HTTP adapter development
- **[CLAUDE.md](CLAUDE.md)** - Architecture, development workflow, gotchas
- **[Model Registry & Picker](docs/model-registry-and-picker.md)** - Managing allowlisted models and MCP picker tools

### Reference
- **[Troubleshooting](docs/troubleshooting/http-adapters.md)** - HTTP adapter issues
- **[Decision Graph Docs](docs/decision-graph/)** - Advanced memory features

## Development

### Running Tests

```bash
pytest tests/unit -v                    # Unit tests (fast)
pytest tests/integration -v -m integration  # Integration tests
pytest --cov=. --cov-report=html       # Coverage report
```

See [CLAUDE.md](CLAUDE.md) for development workflow and architecture notes.

### Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature`)
3. Write tests first (TDD workflow)
4. Implement feature
5. Ensure all tests pass
6. Submit PR with clear description

## License

MIT License - see LICENSE file

## Credits

Forged in the fires of digital ambition with:
- [MCP SDK](https://modelcontextprotocol.io/) - The protocol that binds AI to human will
- [Pydantic](https://docs.pydantic.dev/) - Validates our cosmic data structures
- [pytest](https://pytest.org/) - Ensures the council doesn't descend into chaos

Born from the vision of AI models actually talking to each other, not just shouting into the void in parallel.

---

## Status

![Build](https://img.shields.io/badge/build-passing-brightgreen)
![Tests](https://img.shields.io/badge/tests-130%2B%20passing-green)
![Version](https://img.shields.io/badge/version-1.2.1-blue)

**Battle-Tested & Production Ready** - Multi-model deliberative consensus with neural memory networks, structured voting protocols, and adaptive early stopping for those mission-critical technical decisions. The council awaits your command!
