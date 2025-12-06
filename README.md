# Dream Team v2.0

**Multi-agent AI development team with Codex integration, optimized model distribution, and 2025 best practices.**

## What's New in v2.0

- **8 Agents** with optimized model distribution (Opus/Sonnet/Haiku)
- **Codex CLI Integration** - delegate bulk tasks to OpenAI via JetBrains AI
- **3 New Specialist Agents** - code-reviewer, security-tester, tech-researcher
- **6 Output Styles** - formatting presets for different work modes
- **2 New Skills** - codex, systematic-planning
- **Enhanced Security** - hooks block sensitive file access
- **New Commands** - `/codex`, `/parallel-review`, `/quick-fix`

---

## Quick Start

### Option 1: Plugin Installation (Recommended)

```bash
# Add marketplace and install
/plugin marketplace add ashchupliak/dream-team
/plugin install dream-team
```

This installs agents, commands, skills, and hooks automatically.

### Option 2: Manual Installation

```bash
git clone https://github.com/ashchupliak/dream-team.git
cd dream-team
./install.sh
```

> **Note**: Plugin installation includes hooks but NOT `settings.json` or `output-styles/`.
> For full setup including output styles, use `./install.sh` or copy manually.

### Daily Commands (Memorize These 4)

| Command | What It Does |
|---------|--------------|
| `/team <task>` | Full 5-agent workflow |
| `/team-c <task>` | Fast 3-agent for quick fixes |
| `/codex <task>` | Delegate to Codex CLI |
| `/docs <topic>` | Search offline docs |

---

## Agents

### Model Distribution

| Model | Agents | Use Case |
|-------|--------|----------|
| **Opus** | architect, code-reviewer, security-tester | Deep reasoning, complex decisions |
| **Sonnet** | analyst, developer, qa, devops | Implementation, standard tasks |
| **Haiku** | tech-researcher | Fast research, quick lookups |

### Agent Roster (8 Total)

| Agent | Role | Skills |
|-------|------|--------|
| `analyst` | Requirements, research, edge cases | api-design, kotlin-patterns, systematic-planning, codex |
| `architect` | Design, APIs, data models, implementation plan | api-design, kotlin-patterns, nextjs-patterns, jooq-patterns, codex, systematic-planning |
| `developer` | Fullstack implementation (Kotlin/Spring, Next.js) | kotlin-patterns, kotlin-spring-boot, nextjs-patterns, jooq-patterns, prisma-patterns, codex |
| `qa` | Testing, security, code review | kotlin-patterns, nextjs-patterns |
| `devops` | Infrastructure, CI/CD, deployment | k8s-helm, opentelemetry |
| `code-reviewer` | Expert code review (Opus) | kotlin-patterns, api-design, nextjs-patterns |
| `security-tester` | Vulnerability assessment (Opus) | api-design, kotlin-patterns |
| `tech-researcher` | Fast research (Haiku) | - |
| `discovery` | Repository analysis, context generation | - |

---

## Commands

### Team Workflows

| Command | Agents | Best For |
|---------|--------|----------|
| `/team <task>` | 5 (analyst→architect→developer→qa→devops) | Full workflow with EM |
| `/team-a <task>` | 5 + health checks | Production-critical |
| `/team-b <task>` | 5 standard | Normal development |
| `/team-c <task>` | 3 (analyst→developer→qa) | Quick fixes |

### Specialist Commands

| Command | Description |
|---------|-------------|
| `/codex <task>` | Delegate to Codex CLI (JetBrains AI) |
| `/parallel-review` | Code reviewer + security tester in parallel |
| `/quick-fix <issue>` | Fast 3-agent fix workflow |
| `/review` | Code review on current branch/PR |
| `/security-audit` | Comprehensive security scan |
| `/investigate <issue>` | Parallel investigation agents |

### Build & Deploy

| Command | Description |
|---------|-------------|
| `/build` | Build with quality checks |
| `/test [scope]` | Run tests (unit/integration/e2e/all) |
| `/deploy <env>` | Deploy to staging/prod |
| `/hotfix` | Emergency production fix |
| `/new-feature` | Full feature workflow |
| `/discover` | Analyze repo, generate context files |

---

## Codex Integration

The team can delegate tasks to Codex CLI for parallel AI processing.

### Setup

1. Install Codex CLI:
   ```bash
   npm install -g @openai/codex@latest
   ```

2. Configure JetBrains AI staging in `~/.codex/config.toml`:
   ```toml
   [model_providers.jbai-staging]
   name = "JetBrains AI (Staging)"
   base_url = "https://api.stgn.jetbrains.ai/user/v5/llm/openai/v1"
   env_http_headers = { "Grazie-Authenticate-JWT" = "GRAZIE_STAGING_TOKEN" }
   wire_api = "responses"
   ```

3. Set token:
   ```bash
   export GRAZIE_STAGING_TOKEN="your-token"
   ```

### When Agents Use Codex

Architect and Developer can auto-delegate:
- Large-scale refactoring (10+ files)
- Bulk code generation (DTOs, tests)
- Pattern-based transformations
- Codebase analysis

---

## Skills Library (13)

| Skill | Description |
|-------|-------------|
| `kotlin-patterns` | Kotlin idioms for Orca |
| `kotlin-spring-boot` | Spring Boot 3.x patterns |
| `jooq-patterns` | Type-safe SQL queries |
| `nextjs-patterns` | Next.js 15 App Router |
| `prisma-patterns` | Prisma ORM |
| `api-design` | REST API principles |
| `grpc-protobuf` | Service communication |
| `flyway-migrations` | Database migrations |
| `k8s-helm` | Kubernetes/Helm |
| `opentelemetry` | Observability |
| `tanstack-query` | React Query |
| `codex` | **NEW** - Codex CLI delegation |
| `systematic-planning` | **NEW** - 4-phase planning |

---

## Output Styles (6)

Formatting presets in `output-styles/`:

| Style | Use Case |
|-------|----------|
| `systematic-debugger` | Minimal change debugging |
| `bug-hunter` | Severity-based bug reports |
| `concise-executor` | Minimum words, maximum action |
| `teaching-mode` | Educational explanations |
| `structured-reporter` | Tables, status indicators |
| `pair-programmer` | Collaborative thinking |

---

## Security

### Protected Files

Hooks automatically block access to:
- `.env*` files
- `*secret*` files
- `credentials*` files

### Hooks

| Hook | Action |
|------|--------|
| `SessionStart` | Shows team status |
| `PostToolUse` | Logs file changes |
| `PreToolUse` | Blocks sensitive files |
| `PreCompact` | Preserves team state |
| `Stop` | Logs session end |

---

## Discovery Workflow

Run `/discover` once per project to generate context:

```
/discover
     │
     ▼
┌─────────────────────────┐
│ Scans repository        │
│ Identifies tech stack   │
│ Extracts code patterns  │
│ Documents conventions   │
└─────────────────────────┘
     │
     ▼
.claude/context/
├── PROJECT.md
├── PATTERNS.md
└── CONVENTIONS.md
```

---

## Installation Options

### Full Installation

```bash
git clone https://github.com/ashchupliak/dream-team.git
cd dream-team
cp -r agents/ ~/.claude/agents/
cp -r commands/ ~/.claude/commands/
cp -r skills/ ~/.claude/skills/
cp -r output-styles/ ~/.claude/output-styles/
cp settings.json ~/.claude/
```

### Per-Project

```bash
cp -r dream-team/agents/ ./project/.claude/agents/
cp -r dream-team/commands/ ./project/.claude/commands/
# etc.
```

---

## Recommended MCP Servers

```bash
# GitHub integration
claude mcp add github -- npx -y @modelcontextprotocol/server-github

# Context7 - library docs
claude mcp add context7 -- npx -y @upstash/context7-mcp

# Sequential thinking
claude mcp add sequential-thinking -- npx -y @anthropic/mcp-server-sequential-thinking
```

---

## Changelog

### v2.0.0 (2025-12-07)

**New Agents:**
- `code-reviewer` (Opus) - Expert code review
- `security-tester` (Opus) - Vulnerability assessment
- `tech-researcher` (Haiku) - Fast research

**New Commands:**
- `/codex` - Codex CLI integration
- `/parallel-review` - Parallel code + security review
- `/quick-fix` - Fast 3-agent workflow

**New Skills:**
- `codex` - Codex CLI delegation
- `systematic-planning` - 4-phase planning

**New Output Styles:**
- 6 formatting presets

**Improvements:**
- Optimized model distribution (Opus/Sonnet/Haiku)
- Security hooks for sensitive files
- Enhanced settings with deny rules
- All agents now have Bash access for Codex

### v1.0.0 (2025-12-03)

- Initial release with 6 agents
- Team workflows (team, team-a, team-b, team-c)
- 11 skills
- Discovery-first workflow

---

## License

MIT
