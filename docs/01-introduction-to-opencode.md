# 01-introduction-to-opencode.md

## What is OpenCode?

OpenCode is an interactive Command Line Interface (CLI) agent designed to assist developers with a wide range of software engineering tasks. It acts as an intelligent pair programmer, capable of understanding your requests, analyzing your codebase, and executing precise actions using a suite of specialized tools.

Unlike traditional text-based AI assistants, OpenCode operates directly within your terminal, interacting with your project files and running commands in a real environment. This allows it to:

*   **Understand Context:** OpenCode learns from your project's structure, existing code, and your conversation history to provide relevant and accurate assistance.
*   **Execute Actions:** It doesn't just suggest code; it can read files, write new ones, edit existing code, run bash commands, search for patterns, and even delegate complex tasks to specialized sub-agents.
*   **Adhere to Conventions:** OpenCode is designed to follow the established conventions of your project, ensuring that any changes it makes seamlessly integrate with your existing codebase.

## Core Philosophy: Tool-Based Interaction and Contextual Understanding

OpenCode's power stems from two fundamental principles:

1.  **The Agent-Tool Model:** OpenCode operates as an intelligent agent that leverages a variety of internal "tools" to perform tasks. Each tool is designed for a specific purpose (e.g., `read` for reading files, `bash` for running shell commands, `edit` for modifying code). When you give OpenCode a task, it intelligently determines which tools to use, in what sequence, and with what arguments, to achieve the desired outcome. This modular approach allows for robust and verifiable actions.

2.  **Contextual Understanding:** OpenCode maintains a persistent understanding of the conversation and the codebase. This includes:
    *   **Conversation History:** It remembers previous instructions, questions, and outputs, allowing for natural, multi-turn interactions.
    *   **File System Awareness:** Through tools like `glob` and `grep`, it can quickly understand the layout of your project, locate relevant files, and search for specific code patterns.
    *   **Project Conventions:** By analyzing existing code, OpenCode aims to match your project's coding style, naming conventions, and architectural patterns when making modifications.

## Safety and Control

OpenCode is built with safety and user control in mind:

*   **Command Previews:** Before executing any command that modifies your file system or system state (especially `bash` commands), OpenCode will often provide a preview of the command and its potential impact.
*   **Explicit Confirmations:** For critical or potentially destructive actions, OpenCode will prompt for your explicit confirmation before proceeding.
*   **Irreversible Actions:** While OpenCode strives for safety, it's essential to understand that certain `bash` commands (like `rm -rf`) are irreversible. OpenCode will warn you about such commands.
*   **Structured Output:** Tool outputs are presented clearly, making it easy to track OpenCode's actions and verify its work.

By combining an intelligent agent with a powerful set of tools and a focus on safety, OpenCode empowers developers to automate repetitive tasks, accelerate development, and maintain high code quality directly from their command line.
