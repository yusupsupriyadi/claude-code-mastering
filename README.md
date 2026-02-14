# Claude Code Mastering

A batteries-included `.claude/` configuration boilerplate for [Claude Code](https://docs.anthropic.com/en/docs/claude-code). Drop it into any project and get a structured, opinionated development workflow powered by MCP tools, slash commands, custom agents, spec-driven development, and more.

## ![What's Inside](https://img.shields.io/badge/What's_Inside-7c3aed?style=for-the-badge)

| Category | Count | Description |
|----------|-------|-------------|
| **Rules** | 7 | Contextual coding standards (backend, frontend, infra, code style, etc.) |
| **Commands** | 16 | Slash commands for builds, tests, linting, deploys, bugs, and specs |
| **Agents** | 9 | Specialized sub-agents (code reviewer, debugger, tester, terraform, etc.) |
| **Skills** | 3 | Auto-activating assistants (API development, DB migration, security review) |
| **Templates** | 9 | Structured templates for specs, bugs, and design documents |
| **MCP Servers** | 3 | Sequential Thinking, Serena (LSP code intelligence), Context7 (library docs) |

## ![How It Works](https://img.shields.io/badge/How_It_Works-16a34a?style=for-the-badge)

Every command you give flows through three MCP servers working together:

<p align="center">
  <img width="1200" height="568" alt="image" src="https://github.com/user-attachments/assets/c415fe89-f58e-40cc-91c6-36480f8f23a0" />
</p>

**The flow:**

1. **You give a command** — a task, bug fix, feature request, or question
2. **Sequential Thinking** analyzes the problem step-by-step, consulting **Context7** for up-to-date library documentation when needed
3. **Serena** takes over for code execution:
   - **(1) Read** — loads previous context from memory (`list_memories` → `read_memory`)
   - **(2) Execute** — navigates and edits code using LSP-powered semantic tools
   - **(3) Create** — saves new context to memory for future sessions (`write_memory`)

This creates a **persistent, intelligent coding loop** — Claude remembers what it did last session, thinks before acting, and always uses current documentation.

---

## ![One-Click Setup](https://img.shields.io/badge/One--Click_Setup_(Copy--Paste_to_AI)-ea580c?style=for-the-badge)

The fastest way to get started. Copy the prompt below and paste it into **Claude Code** inside your project directory:

```
Set up the Claude Code Mastering boilerplate in this project. Follow these steps:

1. Clone the boilerplate repo to a temp directory and copy the config files:
   - git clone https://github.com/yusupsupriyadi/claude-code-mastering.git /tmp/claude-code-mastering
   - Copy the .claude/ folder, .mcp.json, and CLAUDE.md from /tmp/claude-code-mastering into this project root
   - Remove the temp clone: rm -rf /tmp/claude-code-mastering

2. After copying, ask me the following questions to customize the boilerplate:
   a. "What is your project name?" → Replace all "your-project-" placeholders in .claude/ files
   b. "What tech stack are you using?" (e.g., Python/FastAPI backend, React frontend, Terraform infra, etc.)
      → Remove irrelevant components:
        - No backend? Delete .claude/commands/backend/, remove backend section from .claude/rules/deployment.md
        - No frontend? Delete .claude/commands/frontend/, .claude/rules/frontend.md, .claude/agents/frontend-builder.md
        - No infrastructure? Delete .claude/commands/infra/, .claude/rules/infrastructure.md, .claude/agents/terraform-planner.md
   c. "What is your preferred communication language?" → Update the language setting in CLAUDE.md (default is Bahasa Indonesia)
   d. "Do you use AWS? If yes, what are your AWS profile names for dev and prod?" → Replace your-dev-profile and your-prod-profile in .claude/ files. If no AWS, remove infra-related files.

3. After customization, show me a summary of:
   - Which files were copied
   - Which components were removed (if any)
   - Which placeholders were replaced
   - What slash commands are available (list all /command-name)

4. Finally, verify the setup by checking that .claude/ folder exists with the correct structure.
```

> **Note**: This works with Claude Code CLI. For other AI assistants, you may need to adjust the git/file commands to match their tool capabilities.

---

## ![Manual Setup](https://img.shields.io/badge/Manual_Setup-2563eb?style=for-the-badge)

### Prerequisites

- [Claude Code CLI](https://docs.anthropic.com/en/docs/claude-code) installed and authenticated
- [Node.js](https://nodejs.org/) 18+ (for MCP servers)
- [Python](https://www.python.org/) 3.11+ with `uvx` (for Serena MCP) — install via [uv](https://docs.astral.sh/uv/)

### Step-by-Step

**1. Clone or copy into your project**

```bash
# Option A: Clone as a starting point for a new project
git clone https://github.com/yusupsupriyadi/claude-code-mastering.git my-project
cd my-project
rm -rf .git && git init

# Option B: Copy into an existing project
git clone https://github.com/yusupsupriyadi/claude-code-mastering.git /tmp/ccm
cp -r /tmp/ccm/.claude your-project/.claude
cp /tmp/ccm/.mcp.json your-project/.mcp.json
cp /tmp/ccm/CLAUDE.md your-project/CLAUDE.md
rm -rf /tmp/ccm
```

**2. Customize for your project**

Open `CLAUDE.md` and review the rules. The defaults work for most full-stack projects. Key things to customize:

- **Communication language** — defaults to Bahasa Indonesia, change if needed
- **Git rules** — review commit message conventions
- **MCP tool preferences** — adjust workflow to your team's style

Open `.claude/rules/` and adjust domain-specific rules:

```
.claude/rules/
├── backend.md          # Backend dev rules (Docker, testing)
├── frontend.md         # Frontend dev rules (npm, builds)
├── infrastructure.md   # Terraform/IaC rules (AWS profiles)
├── deployment.md       # Pre-deploy checklists
├── documentation.md    # Documentation standards
├── code-style.md       # Code style conventions
└── planning.md         # Task planning requirements
```

> **Tip**: Files in `rules/` can have `paths:` frontmatter to scope them to specific directories. Add this back if you want rules to only trigger for certain folders (e.g., `paths: ["backend/**/*"]`).

**3. Configure infrastructure placeholders**

Search for `your-` placeholders and replace with your actual values:

```bash
# Find all placeholders
grep -r "your-" .claude/
```

Common placeholders to replace:
- `your-dev-profile` → your AWS dev profile name
- `your-prod-profile` → your AWS production profile name
- `your-project-` → your project name prefix (for ECS clusters, CloudWatch, etc.)

**4. Verify MCP servers work**

```bash
# Start Claude Code — MCP servers auto-initialize
claude

# Inside Claude Code, test each MCP:
# Sequential Thinking — automatic, used on every request
# Serena — type: /backend:test or ask Claude to analyze code
# Context7 — ask Claude about any library docs
```

**5. (Optional) Set up Serena project**

If you want Serena's full LSP-powered code intelligence:

```bash
# Inside Claude Code, run:
# > activate_project with your project path
# > onboarding to index the codebase
```

## ![Project Structure](https://img.shields.io/badge/Project_Structure-475569?style=for-the-badge)

```
your-project/
├── .claude/
│   ├── agents/                    # Specialized sub-agents
│   │   ├── backend-tester.md      # Test execution & analysis
│   │   ├── code-reviewer.md       # Code quality reviews
│   │   ├── debugger.md            # Bug investigation
│   │   ├── frontend-builder.md    # Frontend build & lint fixes
│   │   ├── terraform-planner.md   # Infrastructure planning
│   │   ├── spec-design-validator.md
│   │   ├── spec-requirements-validator.md
│   │   ├── spec-task-executor.md
│   │   └── spec-task-validator.md
│   │
│   ├── commands/                  # Slash commands (/command-name)
│   │   ├── backend/
│   │   │   ├── lint.md            # /backend:lint
│   │   │   ├── test.md            # /backend:test
│   │   │   ├── migrate.md         # /backend:migrate
│   │   │   └── security.md        # /backend:security
│   │   ├── frontend/
│   │   │   ├── build.md           # /frontend:build
│   │   │   ├── lint.md            # /frontend:lint
│   │   │   ├── test.md            # /frontend:test
│   │   │   └── storybook.md       # /frontend:storybook
│   │   ├── infra/
│   │   │   ├── plan.md            # /infra:plan
│   │   │   ├── apply.md           # /infra:apply
│   │   │   └── status.md          # /infra:status
│   │   ├── deploy-check.md        # /deploy-check
│   │   ├── bug-create.md          # /bug-create
│   │   ├── bug-analyze.md         # /bug-analyze
│   │   ├── bug-fix.md             # /bug-fix
│   │   ├── bug-verify.md          # /bug-verify
│   │   ├── bug-status.md          # /bug-status
│   │   ├── spec-create.md         # /spec-create
│   │   ├── spec-execute.md        # /spec-execute
│   │   ├── spec-list.md           # /spec-list
│   │   ├── spec-status.md         # /spec-status
│   │   └── spec-steering-setup.md # /spec-steering-setup
│   │
│   ├── rules/                     # Contextual coding rules
│   │   ├── backend.md
│   │   ├── frontend.md
│   │   ├── infrastructure.md
│   │   ├── deployment.md
│   │   ├── documentation.md
│   │   ├── code-style.md
│   │   └── planning.md
│   │
│   ├── skills/                    # Auto-activating assistants
│   │   ├── api-development/
│   │   ├── database-migration/
│   │   └── security-review/
│   │
│   ├── templates/                 # Structured document templates
│   │   ├── bug-report-template.md
│   │   ├── bug-analysis-template.md
│   │   ├── bug-verification-template.md
│   │   ├── requirements-template.md
│   │   ├── design-template.md
│   │   ├── tasks-template.md
│   │   ├── product-template.md
│   │   ├── tech-template.md
│   │   └── structure-template.md
│   │
│   └── settings.local.json       # MCP server enablement
│
├── .mcp.json                      # MCP server configuration
└── CLAUDE.md                      # Master rules & workflow
```

## ![Features](https://img.shields.io/badge/Features-0891b2?style=for-the-badge)

### Slash Commands

Run these inside Claude Code:

| Command | Description |
|---------|-------------|
| `/backend:lint` | Run backend code quality checks (black, ruff, mypy) |
| `/backend:test` | Run backend tests via Docker Compose |
| `/backend:migrate` | Create or run database migrations |
| `/backend:security` | Run security checks before deployment |
| `/frontend:build` | Full frontend build with quality checks |
| `/frontend:lint` | Lint and format frontend code |
| `/frontend:test` | Run frontend tests with Vitest |
| `/frontend:storybook` | Start Storybook dev server |
| `/infra:plan` | Run Terraform plan for an environment |
| `/infra:apply` | Apply Terraform changes (with confirmation) |
| `/infra:status` | Check infrastructure status |
| `/deploy-check` | Run all pre-deployment checks |

### Bug Workflow

A streamlined 4-phase workflow for tracking and resolving bugs:

```
/bug-create login-timeout "Users getting logged out too quickly"
/bug-analyze login-timeout
/bug-fix login-timeout
/bug-verify login-timeout
/bug-status login-timeout
```

Each phase creates structured documents in `.claude/bugs/{bug-name}/`.

### Spec-Driven Development

A full specification workflow for building features methodically:

```
/spec-create user-auth "Allow users to sign up and log in"
/spec-execute user-auth
/spec-status user-auth
/spec-list
```

The workflow guides you through:
1. **Requirements** — User stories with acceptance criteria
2. **Design** — Architecture with Mermaid diagrams
3. **Tasks** — Atomic, agent-friendly implementation tasks
4. **Execution** — Step-by-step implementation with validation

### ![MCP Servers](https://img.shields.io/badge/MCP_Servers-ca8a04?style=flat-square)

Three MCP servers power the intelligent workflow. All are configured in `.mcp.json` and auto-start with Claude Code.

#### 1. Sequential Thinking

> **Repo**: [modelcontextprotocol/servers/sequentialthinking](https://github.com/modelcontextprotocol/servers/tree/main/src/sequentialthinking) | **npm**: [@modelcontextprotocol/server-sequential-thinking](https://www.npmjs.com/package/@modelcontextprotocol/server-sequential-thinking) | **License**: MIT

An official MCP server from the [Model Context Protocol](https://modelcontextprotocol.io/) team that enables dynamic and reflective problem-solving through structured thought sequences. Claude breaks down complex problems into manageable steps with support for **revision** (correcting earlier thoughts) and **branching** (exploring alternative paths).

**What it does:**
- Forces step-by-step analysis before any coding action
- Supports revising previous thoughts when understanding changes
- Enables branching into alternative solution paths
- Tracks thought history for context continuity

**Key tool:** `sequentialthinking` — takes a thought, returns structured analysis with support for `isRevision`, `branchFromThought`, and `needsMoreThoughts` parameters.

#### 2. Serena

> **Repo**: [oraios/serena](https://github.com/oraios/serena) | **Install**: `uvx --from git+https://github.com/oraios/serena serena start-mcp-server` | **License**: MIT

A powerful coding agent toolkit by [Oraios AI](https://github.com/oraios) that provides **semantic code retrieval and editing** powered by Language Server Protocol (LSP). Unlike basic file operations, Serena understands code structure — it navigates and edits code the way a developer using an IDE would.

**What it does:**
- **Semantic navigation**: Find symbols, references, and type hierarchies across the codebase
- **Precise editing**: Replace symbol bodies, insert before/after symbols, rename across the entire project
- **30+ language support**: Python, TypeScript, Java, Go, Rust, C#, and many more
- **Built-in memory**: Persistent context storage across sessions (`write_memory`, `read_memory`)
- **Project onboarding**: Automatic project structure analysis

**Key tools:** `find_symbol`, `find_referencing_symbols`, `rename_symbol`, `replace_symbol_body`, `write_memory`, `read_memory`, `onboarding`, `search_for_pattern`

**Optional backend**: Also supports [JetBrains IDE plugin](https://github.com/oraios/serena) for even deeper code analysis via IntelliJ/WebStorm/PyCharm.

#### 3. Context7

> **Repo**: [upstash/context7](https://github.com/upstash/context7) | **npm**: [@upstash/context7-mcp](https://www.npmjs.com/package/@upstash/context7-mcp) | **License**: MIT

An MCP server by [Upstash](https://upstash.com/) that delivers **up-to-date, version-specific library documentation** directly to Claude. Instead of relying on training data (which may be outdated), Context7 pulls real documentation and working code examples from official sources.

**What it does:**
- Fetches current documentation for any library (React, FastAPI, SQLAlchemy, Prisma, Next.js, etc.)
- Returns version-specific API references and code examples
- Eliminates hallucinated or outdated API usage
- Free to use, no API key required for basic usage

**Key tools:**
- `resolve-library-id` — resolves a library name (e.g., "react") into a Context7-compatible ID
- `get-library-docs` — fetches documentation for a specific topic from the resolved library

### ![Custom Agents](https://img.shields.io/badge/Custom_Agents-dc2626?style=flat-square)

Specialized sub-agents that Claude delegates to:

| Agent | Model | Purpose |
|-------|-------|---------|
| `backend-tester` | Sonnet | Execute tests, analyze failures, suggest fixes |
| `code-reviewer` | Sonnet | Review code quality, security, performance |
| `debugger` | Sonnet | Track down bugs across the full stack |
| `frontend-builder` | Sonnet | Fix build errors, TypeScript issues, lint problems |
| `terraform-planner` | Sonnet | Analyze Terraform plans, evaluate change impacts |
| `spec-*-validator` | Sonnet | Validate spec documents for quality |
| `spec-task-executor` | Sonnet | Execute individual spec tasks |

## ![Customization Guide](https://img.shields.io/badge/Customization_Guide-c026d3?style=for-the-badge)

### Adding New Rules

Create a new `.md` file in `.claude/rules/`:

```markdown
# Your Custom Rules

- Follow project naming conventions
- Write tests for all new features
- Use dependency injection pattern
- ...
```

### Adding New Commands

Create a new `.md` file in `.claude/commands/`:

```markdown
---
description: Run database seed script
allowed-tools: Bash(docker compose exec:*)
argument-hint: "[environment: dev|test]"
---

Seed the database for the specified environment.

## Execute:
\`\`\`bash
docker compose exec app uv run python scripts/seed.py $1
\`\`\`
```

Then use it in Claude Code as `/your-command-name`.

### Adding New Agents

Create a new `.md` file in `.claude/agents/`:

```markdown
---
name: my-agent
description: What this agent does
model: sonnet
tools: [Read, Grep, Bash(specific:*)]
---

## Agent Instructions

Your detailed instructions here...
```

### Adding New Skills

Create a new directory in `.claude/skills/` with a `SKILL.md`:

```markdown
---
name: my-skill
description: Auto-activates when [trigger conditions]. Keywords: keyword1, keyword2
allowed-tools: Read, Write, Grep
---

## Skill Instructions

Your skill's specialized knowledge and instructions...
```

### Removing Unused Components

If your project doesn't have certain layers, simply delete the corresponding files:

- **No backend?** Delete `commands/backend/`, remove backend section from `rules/deployment.md`
- **No infrastructure?** Delete `commands/infra/`, `rules/infrastructure.md`, `agents/terraform-planner.md`
- **No frontend?** Delete `commands/frontend/`, `rules/frontend.md`, `agents/frontend-builder.md`

## ![Requirements](https://img.shields.io/badge/Requirements_by_Stack-4f46e5?style=for-the-badge)

| Stack | Required Tools |
|-------|---------------|
| **Backend (Python)** | Docker, Docker Compose, uv, Python 3.11+ |
| **Frontend (Node)** | Node.js 18+, npm |
| **Infrastructure** | Terraform, AWS CLI, Make |
| **MCP: Serena** | Python 3.11+, uvx |
| **MCP: Sequential Thinking** | Node.js 18+, npx |
| **MCP: Context7** | Node.js 18+, npx |

## ![FAQ](https://img.shields.io/badge/FAQ-64748b?style=for-the-badge)

**Q: Do I need all three MCP servers?**
A: Sequential Thinking and Context7 work out of the box with just Node.js. Serena requires Python/uvx but provides the most powerful code intelligence. You can disable any server in `.claude/settings.local.json`.

**Q: Can I use this with a monorepo?**
A: Yes. Use `paths:` frontmatter in rules to scope them to specific directories. Commands and agents are already framework-agnostic.

**Q: How do I disable a specific command or agent?**
A: Simply delete the `.md` file. Claude Code discovers them at startup.

**Q: The MCP servers aren't starting. What do I check?**
A: Verify Node.js 18+ and Python 3.11+ are installed. Check `.mcp.json` paths. Run `npx -y @modelcontextprotocol/server-sequential-thinking` manually to test.

## ![Contributing](https://img.shields.io/badge/Contributing-16a34a?style=for-the-badge)

Contributions are welcome! Feel free to open issues or submit pull requests at [github.com/yusupsupriyadi/claude-code-mastering](https://github.com/yusupsupriyadi/claude-code-mastering).

## ![License](https://img.shields.io/badge/License-334155?style=for-the-badge)

MIT
