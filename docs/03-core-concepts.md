# 03-core-concepts.md

OpenCode operates on a powerful foundation built around an agent-tool model, deep contextual understanding, and a systematic approach to planning and execution. Understanding these core concepts is key to effectively leveraging OpenCode for your development tasks.

## The Agent-Tool Model

At its heart, OpenCode is an intelligent agent that interacts with your environment through a set of specialized tools. Instead of directly executing every command you type, OpenCode interprets your request and decides which of its available tools are best suited to fulfill it. This approach provides several benefits:

*   **Modularity:** Each tool has a clear, well-defined purpose, making OpenCode's actions predictable and robust.
*   **Safety:** Tools can enforce specific safety checks and permissions (e.g., preventing accidental overwrites, requiring absolute paths).
*   **Verifiability:** You can see exactly which tool OpenCode is using and what arguments it's providing, allowing you to understand and confirm its actions.

### Detailed Explanation of Core Tools

Here are some of the fundamental tools OpenCode uses, which you'll interact with directly or indirectly:

*   **`read`**: Reads the content of a file or directory.
    *   **Usage:** `opencode read --filePath /path/to/your/file.js`
    *   **Purpose:** Essential for OpenCode to understand the current state of your code, configuration, or any text-based content. Always returns absolute paths, and supports offset/limit for large files.

*   **`write`**: Writes content to a file, overwriting it if it already exists.
    *   **Usage:** `opencode write --filePath /path/to/new/file.js --content "console.log('Hello');"`
    *   **Purpose:** Used for creating new files or completely replacing the content of existing ones. Requires an absolute path.

*   **`edit`**: Performs exact string replacements within a file.
    *   **Usage:** `opencode edit --filePath /path/to/file.js --oldString "oldFunction" --newString "newFunction" --replaceAll true`
    *   **Purpose:** Ideal for precise modifications like renaming variables, updating function calls, or fixing specific lines of code. Can replace all occurrences with `replaceAll: true`.

*   **`bash`**: Executes arbitrary shell commands.
    *   **Usage:** `opencode bash --command "npm install" --description "Install project dependencies"`
    *   **Purpose:** Your gateway to running any terminal command, such as `git` operations, `npm` scripts, `pytest`, `tsc`, `ls`, etc. Always provides a description of the command's intent for clarity.

*   **`glob`**: Finds files based on a glob pattern.
    *   **Usage:** `opencode glob --pattern "src/**/*.js"`
    *   **Purpose:** Quickly locate files that match a specific naming convention or are within certain directories. Useful for understanding project structure or finding relevant files to `read` or `grep`.

*   **`grep`**: Searches file contents using regular expressions.
    *   **Usage:** `opencode grep --pattern "function\s+\w+\(.*\)" --include "*.js"`
    *   **Purpose:** Powerful for finding specific code patterns, function definitions, variable usages, or text strings across multiple files.

*   **`task`**: Launches a new specialized sub-agent to handle complex, multi-step tasks autonomously.
    *   **Usage:** `opencode task --subagent_type "explore" --prompt "Find all API endpoints in the backend and explain their purpose."`
    *   **Purpose:** When a request is too complex for a single tool call or requires deeper reasoning, OpenCode can delegate to specialized sub-agents (e.g., `explore` for codebase analysis, `general` for multi-step tasks).

*   **`question`**: Asks the user questions to gather preferences, clarify ambiguity, or get decisions.
    *   **Usage:** `opencode question --questions "Which framework do you prefer for the UI?" --options "React", "Vue", "Angular"`
    *   **Purpose:** Enables OpenCode to engage in interactive decision-making with you, ensuring its actions align with your preferences.

## Absolute vs. Relative Paths

**Crucial Point:** OpenCode tools that interact with the file system (e.g., `read`, `write`, `edit`) **require absolute file paths**. You must always provide the full path from the root of your filesystem.

*   **Good:** `/Users/youruser/my-project/src/components/Button.js`
*   **Bad:** `src/components/Button.js` (unless you are absolutely certain of the current working directory, and even then, absolute is safer)

When you ask OpenCode to interact with files, it will typically resolve relative paths to absolute paths if it has enough context. However, it's a best practice to provide absolute paths when you can, or use `glob` to find the absolute paths first.

## Contextual Understanding

OpenCode doesn't operate in a vacuum. It builds a rich understanding of its environment through:

*   **Conversation History:** Every interaction, every command, and every output contributes to its understanding of the task at hand.
*   **Codebase Scan:** When you point OpenCode to your project, it can intelligently analyze file structures, common conventions, and existing code patterns using tools like `glob` and `grep`.
*   **Configuration Files:** It can read `package.json`, `requirements.txt`, `webpack.config.js`, etc., to understand dependencies, scripts, and build processes.

This contextual awareness allows OpenCode to make more informed decisions, suggest relevant solutions, and integrate seamlessly with your project.

## Planning and Execution

When you give OpenCode a task, it goes through an internal planning phase:

1.  **Understand:** It parses your request and identifies the core problem or goal.
2.  **Analyze:** It might use tools like `glob` or `grep` to gather necessary information about the codebase or confirm assumptions.
3.  **Plan:** It formulates a sequence of steps, often involving multiple tool calls, to achieve the goal.
4.  **Execute:** It then executes these steps, providing you with the output of each tool call.
5.  **Verify:** After making changes, it often attempts to verify its work by running tests, linters, or build commands.

This systematic approach ensures that OpenCode's actions are deliberate and verifiable.

## Safety Protocols

OpenCode incorporates several safety features to prevent unintended consequences:

*   **Bash Command Explanations:** Before executing any `bash` command, OpenCode provides a brief explanation of what the command does, allowing you to understand its impact.
*   **Confirmation for Destructive Actions:** For commands that could lead to data loss or irreversible changes (e.g., `rm -rf`), OpenCode will typically ask for your explicit confirmation.
*   **Adherence to Project Conventions:** OpenCode prioritizes integrating changes that match your project's existing style, reducing the chance of introducing inconsistencies.
*   **Error Handling:** It is designed to report errors from tool executions, allowing you to debug and adjust your approach.

By understanding these core concepts, you'll be better equipped to formulate effective prompts, interpret OpenCode's actions, and collaborate with it to achieve your software development goals.
