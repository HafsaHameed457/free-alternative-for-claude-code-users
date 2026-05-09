# OpenCode Command Reference

All commands, flags, tools, and configuration options in one place. Bookmark this page!

---

## CLI Flags

```bash
opencode [command] [options]
```

| Flag | Description | Example |
| :--- | :--- | :--- |
| `--version` | Show installed version | `opencode --version` |
| `--help` | Show help information | `opencode --help` |
| `--model <name>` | Specify model to use | `opencode --model claude-3-5-sonnet` |
| `--context <level>` | Set context level (low, medium, high) | `opencode --context high` |
| `--temperature <value>` | Set model temperature (0-1) | `opencode --temperature 0.7` |
| `--max-tokens <number>` | Set max response tokens | `opencode --max-tokens 4000` |

---

## Core Tools

### read - Read Files

Read file contents with optional offset and limit.

```bash
opencode read --filePath <absolute-path> [--offset <line>] [--limit <lines>]
```

**Examples:**
```bash
opencode read --filePath /Users/name/project/src/App.js
opencode read --filePath /path/to/file.js --offset 50 --limit 100
```

---

### write - Create/Overwrite Files

Write content to a file (overwrites existing).

```bash
opencode write --filePath <absolute-path> --content <content>
```

**Examples:**
```bash
opencode write --filePath /path/to/new.js --content "console.log('Hello');"
opencode write --filePath /path/to/config.json --content '{"key": "value"}'
```

---

### edit - Modify Files

Perform exact string replacement in a file.

```bash
opencode edit --filePath <path> --oldString <string> --newString <string> [--replaceAll <bool>]
```

**Examples:**
```bash
# Single replacement
opencode edit --filePath /path/to/file.js --oldString "oldFunction" --newString "newFunction"

# Replace all occurrences
opencode edit --filePath /path/to/file.js --oldString "oldVar" --newString "newVar" --replaceAll true
```

**Note:** Must match exact string including whitespace and indentation.

---

### bash - Execute Shell Commands

Run terminal commands.

```bash
opencode bash --command <command> [--description <text>] [--timeout <ms>]
```

**Examples:**
```bash
opencode bash --command "npm install" --description "Install dependencies"
opencode bash --command "git status" --description "Show git status"
opencode bash --command "pytest tests/" --timeout 60000
opencode bash --command "npm run build" --description "Build the project"
```

---

### glob - Find Files by Pattern

Find files matching glob patterns.

```bash
opencode glob --pattern <pattern> [--path <directory>]
```

**Examples:**
```bash
# All JS files in src
opencode glob --pattern "src/**/*.js"

# All TypeScript files
opencode glob --pattern "**/*.ts"

# All CSS files in project
opencode glob --pattern "**/*.css"

# Python files in specific directory
opencode glob --pattern "src/**/*.py" --path /path/to/project
```

---

### grep - Search File Contents

Search for patterns in files using regex.

```bash
opencode grep --pattern <regex> [--include <files>] [--path <directory>]
```

**Examples:**
```bash
# Find function definitions
opencode grep --pattern "function\s+\w+\s*\(" --include "*.js"

# Search for specific string
opencode grep --pattern "TODO" --include "*.js,*.ts"

# Find in specific directory
opencode grep --pattern "class\s+\w+" --include "*.py" --path /path/to/project
```

---

### task - Delegate to Sub-Agent

Launch specialized sub-agents for complex tasks.

```bash
opencode task --subagent_type <type> --prompt <task-description> [--task_id <id>]
```

**Available Sub-Agents:**

| Type | Purpose |
| :--- | :--- |
| `explore` | Fast codebase exploration and file finding |
| `general` | Multi-step complex tasks |
| `code-reviewer` | Code review tasks |

**Examples:**
```bash
opencode task --subagent_type "explore" --prompt "Find all API endpoints in the backend"
opencode task --subagent_type "general" --prompt "Fix the bug in auth.js"
opencode task --subagent_type "explore" --prompt "Explain how the login flow works"
```

---

### question - Ask User

Prompt user for input/decision.

```bash
opencode question --questions <question> --options <options> [--multiple <bool>]
```

**Examples:**
```bash
# Single choice
opencode question --question "Which framework?" --options "React", "Vue", "Angular"

# Multiple choice
opencode question --question "Select all that apply?" --options "A", "B", "C" --multiple true
```

---

## Configuration File

OpenCode uses `opencode.json` for configuration. Location: `~/.config/opencode/opencode.json`

### Basic Structure

```json
{
  "model": "claude-3-5-sonnet-20241022",
  "context": "medium",
  "temperature": 0.7,
  "mcpServers": {},
  "plugins": []
}
```

### Complete Schema

```json
{
  "model": "string",
  "context": "low | medium | high",
  "temperature": "number (0-1)",
  "maxTokens": "number",
  "systemPrompt": "string",
  "mcpServers": {
    "server-name": {
      "command": "npx | python | node",
      "args": ["-y", "package-name"],
      "env": {}
    }
  },
  "plugins": ["plugin-name"],
  "excludePatterns": ["*.log", "node_modules/**"],
  "customInstructions": "string"
}
```

---

## Environment Variables

| Variable | Description | Example |
| :--- | :--- | :--- |
| `OPENCODE_MODEL` | Default model | `OPENCODE_MODEL=claude-3-5-sonnet` |
| `OPENCODE_CONFIG` | Config file path | `OPENCODE_CONFIG=/path/to/config.json` |
| `OPENCODE_CONTEXT` | Default context level | `OPENCODE_CONTEXT=high` |
| `OPENCODE_TEMPERATURE` | Default temperature | `OPENCODE_TEMPERATURE=0.5` |
| `ANTHROPIC_API_KEY` | Anthropic API key | `ANTHROPIC_API_KEY=sk-...` |
| `OPENAI_API_KEY` | OpenAI API key | `OPENAI_API_KEY=sk-...` |
| `GOOGLE_API_KEY` | Google API key | `GOOGLE_API_KEY=...` |

---

## Plugin Commands

### Install Plugin

```bash
opencode plugin add <plugin-name>
```

**Examples:**
```bash
opencode plugin add opencode-antigravity-auth
opencode plugin add opencode-supermemory
opencode plugin add @tarquinen/opencode-dcp
```

### List Plugins

```bash
opencode plugin list
```

### Remove Plugin

```bash
opencode plugin remove <plugin-name>
```

---

## MCP Server Configuration

### Common MCP Servers

#### Context7 (Library Docs)
```json
{
  "mcpServers": {
    "ctx7": {
      "command": "npx",
      "args": ["-y", "ctx7", "mcp"]
    }
  }
}
```

#### GitHub MCP
```json
{
  "mcpServers": {
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"]
    }
  }
}
```

#### Puppeteer (Browser Automation)
```json
{
  "mcpServers": {
    "puppeteer": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-puppeteer"]
    }
  }
}
```

#### PostHog (Analytics)
```json
{
  "mcpServers": {
    "posthog": {
      "command": "npx",
      "args": ["-y", "posthog-mcp-server"],
      "env": {
        "POSTHOG_API_KEY": "your-key",
        "POSTHOG_PROJECT_URL": "https://your-project.posthog.com"
      }
    }
  }
}
```

---

## Common Patterns

### Read then Edit

```bash
# 1. Read file first
opencode read --filePath /path/to/file.js

# 2. Then edit
opencode edit --filePath /path/to/file.js --oldString "old" --newString "new"
```

### Grep then Replace

```bash
# 1. Find all occurrences
opencode grep --pattern "getUserData" --include "*.js"

# 2. Replace in each file
opencode edit --filePath /path/to/file1.js --oldString "getUserData" --newString "fetchUserProfile" --replaceAll true
```

### Glob then Read

```bash
# 1. Find files
opencode glob --pattern "src/**/*.ts"

# 2. Read specific file
opencode read --filePath /path/to/src/main.ts
```

### Task for Complex Work

```bash
# Delegate multi-step task
opencode task --subagent_type "general" --prompt "Refactor the auth module. First identify all auth-related files, then rename the functions to follow our naming convention, then run tests to verify."
```

---

## Quick Reference Table

| Task | Command/Pattern |
| :--- | :--- |
| Read file | `opencode read --filePath <absolute-path>` |
| Write file | `opencode write --filePath <path> --content <content>` |
| Edit file | `opencode edit --filePath <path> --oldString <old> --newString <new>` |
| Run command | `opencode bash --command "<cmd>" --description "<desc>"` |
| Find files | `opencode glob --pattern "**/*.ext"` |
| Search code | `opencode grep --pattern "<regex>" --include "*.ext"` |
| Delegate task | `opencode task --subagent_type "<type>" --prompt "<prompt>"` |
| Ask user | `opencode question --question "<q>" --options "A,B,C"` |
| Get help | `opencode --help` |
| Check version | `opencode --version` |

---

## Path Requirements

**Important:** OpenCode tools require **absolute paths** for file operations.

| Good | Bad |
| :--- | :--- |
| `/Users/name/project/src/App.js` | `src/App.js` |
| `/home/user/config.json` | `./config.json` |
| `/var/www/index.html` | `index.html` |

Use `glob` to find absolute paths if unsure:
```bash
opencode glob --pattern "**/App.js"
```

---

## Error Codes

| Code | Meaning | Solution |
| :--- | :--- | :--- |
| `ENOENT` | File not found | Check path is absolute and file exists |
| `EACCES` | Permission denied | Check file permissions |
| `EDIT_ERROR` | String mismatch | Verify exact string in file |
| `TIMEOUT` | Command timed out | Increase timeout or optimize command |

---

For more details, see [Core Concepts](03-core-concepts.md) and [Getting Started](02-getting-started.md).