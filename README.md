# Multi-Stack Claude Code Setup

Claude Code configuration for multi-stack development. Provides **7 slash commands** and **11 specialized AI agents**.

## Supported Stacks

- **Python**: FastAPI, Flask
- **JavaScript/TypeScript**: React, Node.js, Express
- **Go**
- **Rust**
- **Mobile**: Flutter/Dart, Kotlin (Android/AR Core)
- **Database**: PostgreSQL (AWS RDS)
- **Infrastructure**: AWS CLI

## What's Inside

### Commands (7)

| Command | Description |
|---------|-------------|
| `/new-task` | Analyze task complexity and create implementation plan |
| `/code-optimize` | Performance optimization (multi-language) |
| `/code-cleanup` | Refactoring and cleanup |
| `/feature-plan` | Feature implementation planning |
| `/lint` | Run linting and fix issues |
| `/docs-generate` | Generate documentation |
| `/api-test` | Test API endpoints |

### AI Agents (11)

Agents activate automatically based on context - no explicit invocation needed.

**Architecture & Planning**
- **tech-stack-researcher** - Technology choice recommendations with trade-offs
- **system-architect** - Scalable system architecture design
- **backend-architect** - Backend systems with data integrity & security
- **frontend-architect** - Performant, accessible UI architecture
- **requirements-analyst** - Transform ideas into concrete specifications

**Code Quality & Performance**
- **refactoring-expert** - Systematic refactoring and clean code
- **performance-engineer** - Measurement-driven optimization
- **security-engineer** - Vulnerability identification and security standards

**Documentation & Research**
- **technical-writer** - Clear, comprehensive documentation
- **learning-guide** - Teaching programming concepts progressively
- **deep-research-agent** - Comprehensive research with adaptive strategies

### MCP Servers (2)

- **context7** - Up-to-date documentation for any library
- **playwright** - Browser automation and web testing

## Installation

```bash
# Clone
git clone <repo-url>
cd <repo>

# Copy to your Claude Code config
cp -r .claude ~/.claude
```

## Usage

### Planning a Task
```bash
/new-task implement user authentication with JWT
```

### Optimize Code
```bash
/code-optimize path/to/file.py
```

### Research Tech Choices

Just ask questions like:
- "Should I use WebSockets or gRPC?"
- "What's the best ORM for FastAPI?"
- "How should I structure this Go service?"

The tech-stack-researcher agent automatically activates.

## Customization

Edit files in:
- `.claude/commands/` - Slash commands
- `.claude/agents/` - AI agent configurations

## License

MIT
