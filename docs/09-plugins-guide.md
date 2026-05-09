# OpenCode Plugins Guide

Plugins extend OpenCode's capabilities with additional tools, memory, agents, and integrations. This guide covers the best free plugins to supercharge your workflow.

---

## Quick Install Reference

```bash
# Add a plugin
opencode plugin add <plugin-name>

# List installed plugins
opencode plugin list

# Remove a plugin
opencode plugin remove <plugin-name>
```

---

## Essential Plugins

### 1. Super Memory

Persistent memory across all sessions and projects.

**Install:**
```bash
opencode plugin add opencode-supermemory
```

**Best for:**
- Remembering project context across sessions
- Storing shared conventions and preferences
- Maintaining knowledge between different projects

**Features:**
- Remembers shared information across all sessions
- Automatically surfaces relevant context
- Works across multiple projects

---

### 2. Antigravity Auth

Free access to high-end models (Gemini 3.1 Pro, Claude Opus) via Google's Antigravity IDE OAuth.

**Install:**
```bash
opencode plugin add opencode-antigravity-auth
```

**Best for:**
- Using premium models without API costs
- Accessing Claude Opus and Gemini models free
- Budget-conscious developers

**Features:**
- Unlock models via Google Antigravity IDE OAuth
- Completely free access
- No API key required

---

### 3. Websearch Cited

Research with inline citations and source tracking.

**Install:**
```bash
opencode plugin add opencode-websearch-cited
```

**Best for:**
- Research tasks requiring sources
- Verifying information with current data
- Technical documentation with references

**Features:**
- Performs web searches with citations
- Provides source URLs inline
- Trackable references for verification

---

### 4. Dynamic Context Pruning (dcp)

Optimize token usage and speed up responses.

**Install:**
```bash
opencode plugin add @tarquinen/opencode-dcp
```

**Best for:**
- Reducing token costs
- Speeding up responses
- Working with large codebases

**Features:**
- Automatically prunes irrelevant context
- Maintains only relevant information
- Optimizes for performance

---

### 5. Smart Title

Automatically generates meaningful session titles.

**Install:**
```bash
opencode plugin add @tarquinen/opencode-smart-title
```

**Best for:**
- Organizing session history
- Finding past sessions quickly
- Managing multiple concurrent projects

**Features:**
- Analyzes session content
- Generates descriptive titles
- Improves session discoverability

---

### 6. OpenCode PTY

Long-running background terminal processes.

**Install:**
```bash
opencode plugin add opencode-pty
```

**Best for:**
- Running long tasks without blocking
- Managing persistent development servers
- Background compilation and builds

**Features:**
- Launch persistent terminal sessions
- Reattach to running sessions
- Manage multiple background processes

---

### 7. Wakatime Integration

Track AI-assisted coding time and activity.

**Install:** See documentation

**Best for:**
- Tracking time spent on AI-assisted coding
- Activity analytics
- Productivity monitoring

**Features:**
- Records file changes
- Tracks coding time
- Provides activity dashboards

---

### 8. Agent Skills

Load Claude-compatible reusable AI workflows.

**Install:**
```bash
opencode plugin add opencode-agent-skills
```

**Best for:**
- Reusable automation workflows
- Standardized coding patterns
- Team-wide conventions

**Features:**
- Load pre-built skill packages
- Create custom workflows
- Share workflows across projects

---

### 9. Background Agents

Delegate work to asynchronous background agents.

**Install:** See documentation

**Best for:**
- Parallel task execution
- Non-blocking operations
- Complex multi-step workflows

**Features:**
- Persistent context for agents
- Keeps main session unblocked
- Background task management

---

## Advanced Plugins

### 10. Oh My Openagent

All-in-one power pack with multiple enhancements.

**Install:** See official documentation

**Best for:**
- Maximum functionality
- Combined toolset
- Enhanced agent capabilities

**Features:**
- Background agents
- LSP integration
- AST tools
- MCP tools
- Full plugin ecosystem

---

### 11. oh-my-opencode-slim

Token-efficient agent orchestration.

**Install:**
```bash
bunx oh-my-opencode-slim@latest install
```

**Best for:**
- Multi-agent workflows
- Token optimization
- Specialized task routing

**Features:**
- 8 specialized sub-agents
- Automatic task routing
- Lower token usage than full version

---

### 12. OpenCode Ultra

Agent orchestration and self-improvement capabilities.

**Install:**
```bash
bun add opencode-ultra
```

**Best for:**
- Complex multi-agent orchestration
- Autonomous self-improvement
- Advanced agent coordination

**Features:**
- Multi-agent orchestration
- AST-based code search
- Self-improvement capabilities

---

## Plugin Comparison Table

| Plugin | Purpose | Install Command | Key Benefit |
| :--- | :--- | :--- | :--- |
| Super Memory | Persistence | `opencode plugin add opencode-supermemory` | Remember context forever |
| Antigravity Auth | Free Models | `opencode plugin add opencode-antigravity-auth` | Premium models free |
| Websearch Cited | Research | `opencode plugin add opencode-websearch-cited` | Sourced answers |
| dcp | Performance | `opencode plugin add @tarquinen/opencode-dcp` | Faster, cheaper |
| Smart Title | Organization | `opencode plugin add @tarquinen/opencode-smart-title` | Find sessions easily |
| PTY | Background | `opencode plugin add opencode-pty` | Non-blocking tasks |
| Agent Skills | Workflows | `opencode plugin add opencode-agent-skills` | Reusable patterns |
| Oh My Openagent | All-in-one | See docs | Complete toolkit |
| Ultra | Orchestration | `bun add opencode-ultra` | Advanced multi-agent |

---

## Configuration

### Verifying Plugin Installation

```bash
opencode plugin list
```

### Updating Plugins

```bash
# Remove and re-add
opencode plugin remove <plugin-name>
opencode plugin add <plugin-name>
```

---

## Use Case Examples

### Research Task with Citations
```bash
# Enable Websearch Cited plugin
# Then ask:
# "Find the latest best practices for React performance optimization with sources"
```

### Memory Across Sessions
```bash
# Enable Super Memory plugin
# First session: "Remember that we use TypeScript strict mode"
# Later session: "What TypeScript conventions should I follow?"
```

### Faster Context Processing
```bash
# Enable dcp plugin
# Automatically optimizes large codebase interactions
# Reduces tokens and speeds up responses
```

---

## Best Practices

1. **Start with essentials**: Super Memory + dcp for most users
2. **Add as needed**: Only install plugins you actually use
3. **Check compatibility**: Some plugins require specific OpenCode versions
4. **Monitor performance**: Too many plugins can slow startup
5. **Keep updated**: Plugin updates often include fixes and improvements

---

## Troubleshooting

| Issue | Solution |
| :--- | :--- |
| Plugin not loading | Run `opencode plugin list` to verify installation |
| Conflicts between plugins | Remove plugins one by one to identify conflict |
| Performance issues | Limit active plugins to essential ones only |
| Version mismatch | Check plugin documentation for requirements |

---

## Related Sections

- [Command Reference](00-command-reference.md) - Plugin commands
- [MCP Servers](10-mcp-servers.md) - Server integrations
- [AI Models](11-ai-models.md) - Model selection with plugins