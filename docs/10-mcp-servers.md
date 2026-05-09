# MCP Servers Guide

MCP (Model Context Protocol) servers connect OpenCode to external services, APIs, and tools. This guide covers the best free MCP servers and their configurations.

---

## MCP Server Basics

### What is MCP?

MCP servers act as bridges between your AI agent and external services. They expose APIs, databases, and tools as AI-accessible functions.

### Adding MCP Servers

Add servers to your `~/.config/opencode/opencode.json`:

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "package-name"],
      "env": {
        "ENV_VAR": "value"
      }
    }
  }
}
```

---

## Essential MCP Servers

### 1. Context7 - Library Documentation

Access fresh, accurate library docs. Prevents AI from using outdated information.

**Configuration:**
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

**Use when:**
- You need current library documentation
- Working with frameworks (React, Vue, etc.)
- Verifying API references

---

### 2. 0nMCP - Multi-API Access

Comprehensive MCP server providing access to many APIs from a single server.

**Configuration:**
```json
{
  "mcpServers": {
    "0nMCP": {
      "command": "npx",
      "args": ["-y", "0nmcp"]
    }
  }
}
```

**Use when:**
- You need multiple API integrations
- Want unified API access
- Building integrations

---

### 3. GitHub MCP Server

Automate GitHub workflows - PRs, issues, branches, and releases.

**Configuration:**
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

**Environment:**
```json
{
  "env": {
    "GITHUB_TOKEN": "ghp_xxxxxxxxxxxx"
  }
}
```

**Use when:**
- Managing PRs programmatically
- Automating issue workflows
- Repository management

---

### 4. PostHog - Product Analytics

Query product analytics data (free for up to 1M events/month).

**Configuration:**
```json
{
  "mcpServers": {
    "posthog": {
      "command": "npx",
      "args": ["-y", "posthog-mcp-server"],
      "env": {
        "POSTHOG_API_KEY": "your-api-key",
        "POSTHOG_PROJECT_URL": "https://your-project.posthog.com"
      }
    }
  }
}
```

**Use when:**
- Analyzing user behavior
- Building product dashboards
- Querying event data

---

### 5. Chrome DevTools MCP

Integrate Chrome's DevTools directly for browser debugging and automation.

**Configuration:**
```json
{
  "mcpServers": {
    "devtools": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-chrome-devtools"]
    }
  }
}
```

**Use when:**
- Browser debugging
- Page automation
- Performance analysis

---

### 6. Puppeteer MCP Server

Programmatic control over a headless browser.

**Configuration:**
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

**Use when:**
- Browser automation
- Web scraping
- Visual testing

---

### 7. Apify Actors

Run over 3,000 pre-built cloud actors for web scraping and automation.

**Configuration:**
```json
{
  "mcpServers": {
    "apify": {
      "command": "npx",
      "args": ["-y", "apify-mcp-server"]
    }
  }
}
```

**Environment:**
```json
{
  "env": {
    "APIFY_TOKEN": "your-apify-token"
  }
}
```

**Use when:**
- Large-scale web scraping
- Data extraction
- Automation workflows

---

### 8. Supabase MCP

Database management - query, migrate, and manage Supabase databases.

**Configuration:**
```json
{
  "mcpServers": {
    "supabase": {
      "command": "npx",
      "args": ["-y", "supabase-mcp-server"]
    }
  }
}
```

**Environment:**
```json
{
  "env": {
    "SUPABASE_URL": "https://your-project.supabase.co",
    "SUPABASE_KEY": "your-anon-key"
  }
}
```

**Use when:**
- Database queries
- Schema management
- Row operations

---

### 9. MongoDB MCP

Manage MongoDB databases through natural language.

**Configuration:**
```json
{
  "mcpServers": {
    "mongodb": {
      "command": "npx",
      "args": ["-y", "mongodb-mcp-server"]
    }
  }
}
```

**Use when:**
- NoSQL database operations
- Document queries
- Collection management

---

## Development-Focused Servers

### 10. Blender MCP

Automate 3D modeling tasks and control Blender from AI.

**Configuration:**
```json
{
  "mcpServers": {
    "blender": {
      "command": "python",
      "args": ["-m", "blender_mcp"]
    }
  }
}
```

**Use when:**
- 3D modeling automation
- Render pipeline management
- Scene manipulation

---

### 11. FastAPI MCP

Expose FastAPI endpoints to AI agents as tools.

**Configuration:**
```json
{
  "mcpServers": {
    "fastapi": {
      "command": "python",
      "args": ["-m", "fastapi_mcp"]
    }
  }
}
```

**Use when:**
- API endpoint exposure
- Backend integration
- Service orchestration

---

### 12. mcp-devtools

Swiss Army knife for dev tasks - filesystem, databases, and APIs.

**Configuration:**
```json
{
  "mcpServers": {
    "devtools": {
      "command": "npx",
      "args": ["-y", "mcp-devtools"]
    }
  }
}
```

**Use when:**
- General development tasks
- Multiple tool access
- Quick prototyping

---

### 13. Render MCP Server

Deploy, scale, and monitor applications using natural language.

**Configuration:**
```json
{
  "mcpServers": {
    "render": {
      "command": "npx",
      "args": ["-y", "render-mcp-server"]
    }
  }
}
```

**Environment:**
```json
{
  "env": {
    "RENDER_API_KEY": "your-render-api-key"
  }
}
```

**Use when:**
- Production deployments
- Service scaling
- Infrastructure management

---

## Complete Configuration Example

Here's a full `opencode.json` with multiple MCP servers:

```json
{
  "model": "claude-3-5-sonnet-20241022",
  "context": "high",
  "mcpServers": {
    "ctx7": {
      "command": "npx",
      "args": ["-y", "ctx7", "mcp"]
    },
    "github": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-github"],
      "env": {
        "GITHUB_TOKEN": "ghp_xxxxxxxxxxxx"
      }
    },
    "posthog": {
      "command": "npx",
      "args": ["-y", "posthog-mcp-server"],
      "env": {
        "POSTHOG_API_KEY": "phc_xxxxxxxxxxxx",
        "POSTHOG_PROJECT_URL": "https://your-project.posthog.com"
      }
    },
    "puppeteer": {
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-puppeteer"]
    },
    "supabase": {
      "command": "npx",
      "args": ["-y", "supabase-mcp-server"],
      "env": {
        "SUPABASE_URL": "https://your-project.supabase.co",
        "SUPABASE_KEY": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9..."
      }
    }
  },
  "plugins": []
}
```

---

## MCP Server Comparison

| Server | Best For | Command | Key Use |
| :--- | :--- | :--- | :--- |
| **Context7** | Fresh docs | `npx -y ctx7 mcp` | Always accurate info |
| **0nMCP** | Multiple APIs | `npx -y 0nmcp` | Unified API access |
| **GitHub** | Repo automation | `npx -y @modelcontextprotocol/server-github` | PRs, issues, branches |
| **PostHog** | Analytics | `npx -y posthog-mcp-server` | Query events/data |
| **Chrome DevTools** | Browser | `npx -y @modelcontextprotocol/server-chrome-devtools` | Debug, automate |
| **Puppeteer** | Browser | `npx -y @modelcontextprotocol/server-puppeteer` | Headless control |
| **Apify** | Scraping | `npx -y apify-mcp-server` | 3000+ actors |
| **Supabase** | Database | `npx -y supabase-mcp-server` | SQL, migrations |
| **MongoDB** | NoSQL | `npx -y mongodb-mcp-server` | Document queries |
| **Blender** | 3D | `python -m blender_mcp` | 3D automation |
| **FastAPI** | Backend | `python -m fastapi_mcp` | API exposure |
| **Render** | Deploy | `npx -y render-mcp-server` | Cloud deployment |

---

## Best Practices

1. **Start essential**: Context7 + GitHub for most users
2. **Add on demand**: Only add servers you need
3. **Secure tokens**: Use environment variables, not hardcoded
4. **Test individually**: Add one at a time to isolate issues
5. **Keep updated**: MCP servers are frequently updated

---

## Troubleshooting

| Issue | Solution |
| :--- | :--- |
| Server not starting | Verify `npx` is installed and working |
| Authentication errors | Check environment variables are set correctly |
| Server not found | Ensure package name is correct (check npm) |
| Connection timeout | Increase timeout or check network |

---

## Related Sections

- [Command Reference](00-command-reference.md) - MCP config examples
- [Plugins Guide](09-plugins-guide.md) - Plugin integrations
- [Best Practices](06-best-practices.md) - Optimization tips