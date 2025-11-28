# AI Assistant Dream Team

Multi-agent AI development team for AI Assistant CLI with context engineering and specialized skills.

## Quick Start

```bash
# Copy to your AI Assistant config
cp -r agents/ ~/.local/agents/
cp -r commands/ ~/.local/commands/
cp -r skills/ ~/.local/skills/
cp settings.json ~/.local/

# Use a team
/team Add user authentication

# Or use specific team configuration
/team-a Add user authentication  # Full workflow with health checks
```

## What's New

### Context Engineering (v2.0)

The Engineering Manager (`/team`) now uses context engineering best practices:

- **Always asks clarifying questions** before delegating work
- **Progressive context disclosure** - minimal info per phase
- **User assistance patterns** - helps with vague requests
- **Context recovery** - handles compaction gracefully

### Skills Library

11 specialized skills for the Orca tech stack:

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

## Teams

| Command | Agents | Workflow | Use Case |
|---------|--------|----------|----------|
| `/team` | 5 | Context Check > Discover > Design > Do > Verify | **Recommended** - with context engineering |
| `/team-a` | 5 | Health Check > Discover > Design > Do > Verify | Production, complex features |
| `/team-b` | 5 | Discover > Design > Do > Verify | Normal development |
| `/team-c` | 3 | Analyze > Implement > Verify | Quick fixes, prototyping |

## Agents

| Agent | Role | Model |
|-------|------|-------|
| `analyst` | Requirements, research, edge cases | Sonnet |
| `architect` | Design, APIs, data models | Sonnet |
| `developer` | Implementation (Kotlin/Spring, Next.js) | Sonnet |
| `qa` | Testing, security, review | Sonnet |
| `devops` | Infrastructure, CI/CD | Sonnet |

## Slash Commands

| Command | Description |
|---------|-------------|
| `/team` | **NEW** - EM with context engineering |
| `/build` | Build project |
| `/test` | Run tests |
| `/deploy` | Deploy to staging/prod |
| `/review` | Code review |
| `/hotfix` | Emergency fix workflow |
| `/investigate` | Parallel investigation |
| `/security-audit` | Security scan |
| `/new-feature` | Full feature workflow |

## Recommended MCP Servers

```bash
# Sequential Thinking - better complex reasoning
ai mcp add sequential-thinking -- npx -y @anthropic/mcp-server-sequential-thinking

# GitHub - issue/PR integration (reads GITHUB_TOKEN from env)
ai mcp add github -- npx -y @modelcontextprotocol/server-github

# Postgres - database queries
ai mcp add postgres-mcp -- npx -y @crystaldba/postgres-mcp

# Prisma - schema management
ai mcp add prisma -- npx -y prisma-mcp-server
```

### Setting Up GitHub Token (One-Time)

The GitHub MCP server reads `GITHUB_TOKEN` from your environment. Set it once:

```bash
# Add to ~/.zshrc (or ~/.bashrc)
echo 'export GITHUB_TOKEN="ghp_your_token_here"' >> ~/.zshrc
source ~/.zshrc
```

Then GitHub MCP works automatically - no need to pass token every time.

## How Context Engineering Works

1. **You say:** "Fix the authentication"

2. **EM asks:** "I'd like to help fix authentication. To delegate effectively:
   - What specific issue are you seeing?
   - Which auth flow? (login, token refresh, SSO?)
   - When did this start?"

3. **You clarify:** "JWT tokens aren't refreshing, started after last deploy"

4. **EM confirms:** "Got it: JWT refresh failing since last deploy. I'll assign analyst to research the issue. Proceed?"

5. **Work begins** with clear requirements

## File Structure

```
~/.local/
├── settings.json     # Global config
├── agents/           # Agent definitions
├── commands/         # Slash commands
└── skills/           # Technology-specific patterns
    ├── kotlin-spring-boot/
    ├── jooq-patterns/
    ├── nextjs-patterns/
    └── ...
```

## Installation

### Option 1: Full Copy

```bash
git clone https://github.com/ashchupliak/dream-team.git
cd dream-team
cp -r agents/ ~/.local/agents/
cp -r commands/ ~/.local/commands/
cp -r skills/ ~/.local/skills/
cp settings.json ~/.local/
```

### Option 2: Selective

```bash
# Just the context engineering command
cp commands/team.md ~/.local/commands/

# Just the skills
cp -r skills/ ~/.local/skills/
```

## Tips

- Use `/team` for all new work - context engineering catches ambiguity early
- Skills are auto-discovered when agents need them
- State persists in `.local/team-state.md` across context compaction
- Always run VERIFY phase - never skip QA

## License

MIT
