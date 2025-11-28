# AI Assistant Dream Team

Multi-agent AI development team for AI Assistant CLI.

## Quick Start

```bash
# Copy to your AI Assistant config
cp -r agents/ ~/.local/agents/
cp -r commands/ ~/.local/commands/
cp settings.json ~/.local/

# Use a team
/team-a Add user authentication
```

## Teams

| Command | Agents | Workflow | Use Case |
|---------|--------|----------|----------|
| `/team-a` | 5 | Health Check > Discover > Design > Do > Verify | Production, complex features |
| `/team-b` | 5 | Discover > Design > Do > Verify | Normal development |
| `/team-c` | 3 | Analyze > Implement > Verify | Quick fixes, prototyping |

## Agents

| Agent | Role |
|-------|------|
| `analyst` | Requirements, research, edge cases |
| `architect` | Design, APIs, data models |
| `developer` | Implementation |
| `qa` | Testing, security, review |
| `devops` | Infrastructure, CI/CD |

## Other Commands

| Command | Description |
|---------|-------------|
| `/build` | Build project |
| `/test` | Run tests |
| `/deploy` | Deploy to staging/prod |
| `/review` | Code review |
| `/hotfix` | Emergency fix workflow |
| `/investigate` | Parallel investigation |
| `/security-audit` | Security scan |
| `/new-feature` | Full feature workflow |

## How It Works

1. Use `/team-a`, `/team-b`, or `/team-c` with your task
2. AI Assistant coordinates specialized agents
3. Each agent handles their phase
4. Work is tracked in `.local/team-state.md`
5. Results verified before completion

## Files

```
~/.local/
├── settings.json     # Global config
├── agents/           # Agent definitions
└── commands/         # Slash commands
```

## License

MIT
