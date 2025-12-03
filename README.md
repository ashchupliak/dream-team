# AI Assistant Dream Team

Project-agnostic multi-agent AI development team for AI Assistant CLI with context engineering and discovery-first workflow.

## Quick Start

```bash
# Copy to your AI Assistant config
cp -r agents/ ~/.local/agents/
cp -r commands/ ~/.local/commands/
cp -r skills/ ~/.local/skills/
cp settings.json ~/.local/

# Step 1: Discover your project (run once per project)
/discover

# Step 2: Use a team
/team Add user authentication
```

## New: Discovery-First Workflow

The team is now **project-agnostic**. Before using `/team`, run `/discover` to analyze your codebase:

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
┌─────────────────────────┐
│ .local/context/         │
│ ├── PROJECT.md          │  ← Tech stack, structure
│ ├── PATTERNS.md         │  ← Code patterns with examples
│ └── CONVENTIONS.md      │  ← Project conventions
└─────────────────────────┘
     │
     ▼
/team [task]  ← Team reads context files
```

### Why Discovery First?

1. **Works with any project** - Kotlin, TypeScript, Python, Go, etc.
2. **Follows YOUR patterns** - Agents learn from your existing code
3. **Reduces hallucination** - Grounded in discovered context
4. **Persists across sessions** - Context files survive compaction

## Teams

| Command | Agents | Workflow | Use Case |
|---------|--------|----------|----------|
| `/team` | 5 | Context Load → Clarify → Discover → Design → Do → Verify | **Recommended** |
| `/team-a` | 5 | Health Check → Discover → Design → Do → Verify | Production, complex features |
| `/team-b` | 5 | Discover → Design → Do → Verify | Normal development |
| `/team-c` | 3 | Analyze → Implement → Verify | Quick fixes, prototyping |

## Agents

| Agent | Role | Phase |
|-------|------|-------|
| `discovery` | Repository analysis, context generation | Pre-work |
| `analyst` | Requirements, research, edge cases | Phase 1: DISCOVER |
| `architect` | Design, APIs, data models | Phase 2: DESIGN |
| `developer` | Implementation | Phase 3: DO |
| `qa` | Testing, security, review | Phase 4: VERIFY |
| `devops` | Infrastructure, CI/CD | Phase 4: VERIFY (if needed) |

## Slash Commands

| Command | Description |
|---------|-------------|
| `/discover` | **NEW** - Analyze repo, generate context files |
| `/team` | EM with context engineering |
| `/build` | Build project |
| `/test` | Run tests |
| `/deploy` | Deploy to staging/prod |
| `/review` | Code review |
| `/hotfix` | Emergency fix workflow |
| `/investigate` | Parallel investigation |
| `/security-audit` | Security scan |
| `/new-feature` | Full feature workflow |

## Skills Library

11 reusable skills (agents auto-discover when needed):

| Skill | Description |
|-------|-------------|
| `kotlin-spring-boot` | Spring Boot 3.x patterns |
| `jooq-patterns` | Type-safe SQL queries |
| `grpc-protobuf` | Service communication |
| `flyway-migrations` | Database migrations |
| `nextjs-patterns` | Next.js 15 App Router |
| `tanstack-query` | React Query patterns |
| `prisma-patterns` | Prisma ORM |
| `k8s-helm` | Kubernetes/Helm |
| `opentelemetry` | Observability |
| `kotlin-patterns` | Kotlin idioms |
| `api-design` | REST API principles |

## How It Works

### 1. Discovery Phase (Run Once)

```bash
/discover
```

The discovery agent:
- Scans for build files (package.json, build.gradle.kts, etc.)
- Identifies tech stack and dependencies
- Finds code patterns (Controllers, Services, Repositories)
- Documents conventions and build commands

### 2. Team Work (Uses Context)

```bash
/team Add user authentication
```

The Engineering Manager:
1. **Checks context** - Reads `.local/context/` files
2. **Asks questions** - Clarifies ambiguous requests
3. **Delegates** - Assigns work to specialized agents
4. **Coordinates** - Ensures smooth phase transitions
5. **Verifies** - Confirms deliverables meet requirements

Each agent reads the context files and follows YOUR project's patterns.

## Context Engineering

The team uses several patterns to handle ambiguity:

### Clarifying Questions
```
User: "Fix the authentication"

EM: "To delegate effectively:
1. What specific issue are you seeing?
2. Which auth flow? (login, token refresh, SSO?)
3. What should success look like?"
```

### Missing Context Detection
```
EM: "I don't see context files for this project.
Would you like me to run /discover first?"
```

### State Persistence
```
.local/team-state.md tracks:
- Current task and phase
- Key decisions made
- Progress for recovery after compaction
```

## File Structure

```
~/.local/
├── settings.json          # Global config
├── agents/
│   ├── discovery.md       # NEW - Repo analysis
│   ├── analyst.md
│   ├── architect.md
│   ├── developer.md
│   ├── qa.md
│   └── devops.md
├── commands/
│   ├── discover.md        # NEW - Discovery command
│   ├── team.md
│   └── ...
└── skills/                # Reusable pattern libraries
    └── ...

# In your project (generated by /discover):
your-project/
└── .local/
    └── context/
        ├── PROJECT.md     # Tech stack, structure
        ├── PATTERNS.md    # Code patterns
        └── CONVENTIONS.md # Project conventions
```

## Installation

### Full Installation

```bash
git clone https://github.com/ashchupliak/dream-team.git
cd dream-team
cp -r agents/ ~/.local/agents/
cp -r commands/ ~/.local/commands/
cp -r skills/ ~/.local/skills/
cp settings.json ~/.local/
```

### Minimal Installation

```bash
# Just discovery + team workflow
cp commands/discover.md ~/.local/commands/
cp commands/team.md ~/.local/commands/
cp agents/discovery.md ~/.local/agents/
cp agents/analyst.md ~/.local/agents/
cp agents/architect.md ~/.local/agents/
cp agents/developer.md ~/.local/agents/
cp agents/qa.md ~/.local/agents/
```

## Recommended MCP Servers

```bash
# Sequential Thinking - better complex reasoning
ai mcp add sequential-thinking -- npx -y @anthropic/mcp-server-sequential-thinking

# GitHub - issue/PR integration
ai mcp add github -- npx -y @modelcontextprotocol/server-github

# Postgres - database queries
ai mcp add postgres-mcp -- npx -y @crystaldba/postgres-mcp

# Prisma - schema management
ai mcp add prisma -- npx -y prisma-mcp-server
```

### Setting Up GitHub Token

```bash
echo 'export GITHUB_TOKEN="ghp_your_token_here"' >> ~/.zshrc
source ~/.zshrc
```

## Tips

- **Run `/discover` first** on new projects - context makes everything better
- **Context survives sessions** - files persist in `.local/context/`
- **Skills are optional** - agents discover patterns from your code
- **Never skip VERIFY** - QA phase is mandatory

## License

MIT
