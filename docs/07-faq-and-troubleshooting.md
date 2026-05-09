# FAQ and Troubleshooting

Common questions and solutions for OpenCode users.

---

## Frequently Asked Questions

### General

**Q: Is OpenCode free to use?**
A: Yes, the CLI is open source and free. You can bring your own API keys from any LLM provider. Optional paid products (Zen, Go, Enterprise) offer additional features.

**Q: Which models work best with OpenCode?**
A: OpenCode works with any LLM. For coding tasks, Claude 3.5 Sonnet, GPT-4o, and Gemini 1.5 Pro perform well. See [AI Models Guide](11-ai-models.md) for options.

**Q: Can I use OpenCode with my existing API keys?**
A: Yes. Configure your API keys in `opencode.json` or via environment variables. See [AI Models Guide](11-ai-models.md).

**Q: Does OpenCode store my code?**
A: No. OpenCode operates locally and doesn't store your code. Enterprise offers self-hosted deployment with zero data retention.

**Q: Can I use OpenCode with other AI agents?**
A: Yes. Zen and Go products work with any coding agent (Cursor, Windsurf, Claude Code, etc.).

---

### Installation

**Q: How do I install OpenCode?**
A:
```bash
# macOS/Linux
curl -fsSL https://opencode.ai/install | bash

# Or via npm
npm install -g opencode-cli
```

**Q: Where is the config file?**
A: `~/.config/opencode/opencode.json`

**Q: How do I verify installation?**
A:
```bash
opencode --version
```

---

### Configuration

**Q: How do I add an API key?**
A: Add to your config file:
```json
{
  "anthropicApiKey": "sk-ant-..."
}
```
Or use environment variables:
```bash
export ANTHROPIC_API_KEY="sk-ant-..."
```

**Q: How do I change the model?**
A:
```json
{
  "model": "claude-3-5-sonnet-20241022"
}
```

**Q: How do I add MCP servers?**
A: Add to the `mcpServers` section in your config. See [MCP Servers Guide](10-mcp-servers.md).

---

## Common Error Messages

### File Operations

| Error | Cause | Solution |
| :--- | :--- | :--- |
| `ENOENT: no such file or directory` | File doesn't exist | Check path is correct and absolute |
| `EACCES: permission denied` | No read/write permission | Check file permissions |
| `Path must be absolute` | Relative path used | Use full path like `/Users/name/project/file.js` |

---

### Edit Errors

| Error | Cause | Solution |
| :--- | :--- | :--- |
| `oldString not found in content` | String doesn't match exactly | Verify exact text including whitespace |
| `Found multiple matches` | String appears multiple times | Add more context to make it unique |

**Tip:** Copy the exact text from the file to avoid whitespace mismatches.

---

### Command Errors

| Error | Cause | Solution |
| :--- | :--- | :--- |
| `Command failed` | Bash command error | Check command syntax, check output |
| `Timeout exceeded` | Command took too long | Increase timeout or simplify command |
| `Permission denied` | Missing system permissions | Check command requirements |

---

### API Errors

| Error | Cause | Solution |
| :--- | :--- | :--- |
| `Invalid API key` | Key is wrong or expired | Verify key in provider dashboard |
| `Rate limited` | Too many requests | Wait or upgrade plan |
| `Insufficient credits` | No API credits left | Add credits to your account |
| `Model not found` | Wrong model name | Check provider docs for correct name |

---

## Troubleshooting Steps

### 1. Config Issues

```bash
# Validate your config exists
cat ~/.config/opencode/opencode.json

# Check for JSON syntax errors
# (use a JSON validator)
```

### 2. API Key Issues

```bash
# Verify environment variables are set
echo $ANTHROPIC_API_KEY
echo $OPENAI_API_KEY

# Test with explicit key in config
```

### 3. MCP Server Issues

```bash
# Verify npx is installed
npx --version

# Test MCP package exists
npx -y <package-name> --version
```

### 4. Performance Issues

- Reduce context level for simple tasks
- Exclude unnecessary directories in config
- Use faster models for quick tasks

---

## Getting Help

### Official Resources

- **Docs**: [opencode.ai/docs](https://opencode.ai/docs)
- **Discord**: Join the community
- **GitHub Issues**: Report bugs

### Before Reporting an Issue

1. Check this FAQ
2. Verify your configuration
3. Check API key status
4. Try with different model

---

## Related Sections

- [Command Reference](00-command-reference.md) - Tool details
- [Getting Started](02-getting-started.md) - Initial setup
- [AI Models Guide](11-ai-models.md) - Model configuration
- [MCP Servers Guide](10-mcp-servers.md) - Server setup