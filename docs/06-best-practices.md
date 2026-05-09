# Best Practices

Maximize your OpenCode productivity with these proven techniques for prompting, tool usage, and debugging.

---

## Effective Prompting

### 1. Be Specific About Context

**Good:**
"Fix the bug in the login function in src/auth/login.js. The error is that it returns undefined when the password is empty."

**Less Effective:**
"Fix the login bug."

Include:
- File paths
- Expected vs actual behavior
- Error messages if any

---

### 2. Break Complex Tasks into Steps

**Good:**
"First, find all files that use the old API. Then update them to use the new API. Finally, run the tests to verify."

**Less Effective:**
"Migrate our entire codebase to the new API."

OpenCode handles multi-step tasks better when you outline the approach first.

---

### 3. Specify Your Preferences

**Good:**
"Use functional components with hooks, not class components. Follow our existing code style with 2-space indentation."

**Less Effective:**
"Create a React component."

Include:
- Coding style preferences
- Framework/library preferences
- Naming conventions

---

### 4. Set Clear Success Criteria

**Good:**
"Create a function that sorts users by name alphabetically. The function should return an array and handle empty arrays gracefully."

**Less Effective:**
"Make a sorting function."

---

## Leveraging Tools Efficiently

### When to Use Each Tool

| Task | Best Tool | Example |
| :--- | :--- | :--- |
| Read code before editing | `read` | Understand before modifying |
| Find files by name | `glob` | `glob --pattern "**/*.ts"` |
| Find code patterns | `grep` | `grep --pattern "function\s+\w+"` |
| Run commands | `bash` | `npm test`, `git status` |
| Make changes | `edit` | Precise string replacement |
| Create new files | `write` | New components, configs |
| Complex multi-step | `task` | Delegate to sub-agent |

---

### Tool Efficiency Tips

1. **Read before edit**: Always read a file before editing it
2. **Glob before grep**: Find files first, then search within them
3. **Use replaceAll for renames**: When changing names across files
4. **Provide descriptions**: Always include `--description` for bash commands
5. **Use absolute paths**: Required for read/write/edit operations

---

### Combining Tools Effectively

**Pattern: Explore then Act**
```bash
# 1. Explore to find files
opencode glob --pattern "src/**/*.ts"

# 2. Read specific file
opencode read --filePath /path/to/file.ts

# 3. Make changes
opencode edit --filePath /path/to/file.ts --oldString "old" --newString "new"
```

---

## Debugging OpenCode Interactions

### 1. Verify Context Understanding

If OpenCode seems off-track, re-explain:

- Current file locations
- What you've already tried
- What specifically needs to change

### 2. Check Tool Outputs

Always review tool output for:
- File contents from `read`
- Search results from `grep`/`glob`
- Command results from `bash`

### 3. Iterate with Smaller Steps

Instead of:
"Refactor our entire auth system"

Try:
"First, rename the auth.ts file to authentication.ts"

Then:
"Update all imports to point to the new file name"

### 4. Ask for Verification

After changes, ask:
- "Run the tests to verify this works"
- "Show me the changes you made"
- "Confirm the file looks correct"

---

## OpenCode Configuration Tips

### 1. Set Appropriate Context Level

```json
{
  "context": "high"  // Complex tasks
  "context": "low"  // Simple, quick tasks
}
```

### 2. Customize System Prompt

```json
{
  "systemPrompt": "You are working on a TypeScript React project. Always use strict mode. Prefer functional components with hooks."
}
```

### 3. Exclude Unnecessary Files

```json
{
  "excludePatterns": [
    "node_modules/**",
    "*.log",
    ".git/**",
    "dist/**"
  ]
}
```

---

## Productivity Patterns

### 1. Use Task for Complexity

For multi-step work, delegate to a sub-agent:

```bash
opencode task --subagent_type "general" --prompt "Implement a login form with email/password validation. Create the component, add validation logic, and write tests."
```

### 2. Use Question for Decisions

When you need to decide:

```bash
opencode question --question "Which approach should we use?" --options "Option A: REST API", "Option B: GraphQL"
```

### 3. Use Grep to Understand Scope

Before large changes:

```bash
opencode grep --pattern "oldFunctionName" --include "*.js"
```

This shows all files that need updating.

---

## Common Pitfalls to Avoid

| Pitfall | Solution |
| :--- | :--- |
| Vague prompts | Include specific files, errors, expected outcomes |
| Skipping read | Always read before edit |
| Relative paths | Use absolute paths |
| Ignoring tool output | Check results before proceeding |
| Too many changes at once | Break into smaller steps |

---

## Related Sections

- [Command Reference](00-command-reference.md) - All tools
- [Common Workflows](04-common-workflows.md) - Practical examples
- [MCP Servers](10-mcp-servers.md) - Extended capabilities
- [Plugins Guide](09-plugins-guide.md) - Productivity plugins