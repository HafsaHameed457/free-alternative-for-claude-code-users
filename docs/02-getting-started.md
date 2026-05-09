# 02-getting-started.md

## Prerequisites

Before you begin your journey with OpenCode, ensure you have the following installed on your system:

*   **Node.js:** OpenCode is built with Node.js. It is recommended to have a recent LTS (Long Term Support) version installed. You can download it from [nodejs.org](https://nodejs.org/en/download/).
*   **npm (Node Package Manager):** npm is typically installed alongside Node.js. It's used to install OpenCode.
*   **Git:** Essential for version control and cloning repositories. Download it from [git-scm.com](https://git-scm.com/downloads).
*   **A Terminal/Command Prompt:** You'll be interacting with OpenCode directly through your system's terminal (e.g., Terminal on macOS, Git Bash or WSL on Windows, any terminal emulator on Linux).

## Installation Steps

Follow these steps to install OpenCode globally on your system:

1.  **Open your terminal.**

2.  **Install OpenCode using npm:**

    ```bash
    npm install -g opencode-cli
    ```

    *Note: The actual installation command might vary slightly based on the official OpenCode documentation. Always refer to the [official OpenCode documentation](https://www.opencode.com/docs) for the most up-to-date installation instructions.*

3.  **Verify Installation:**

    After the installation is complete, you can verify that OpenCode is correctly installed and accessible by running:

    ```bash
    opencode --version
    ```

    This command should display the installed version of OpenCode. If it shows an error, ensure your npm global bin directory is in your system's PATH.

## Your First Interaction

Let's try a very basic command to get a feel for how OpenCode works.

1.  **Ask for Help:**

    The most fundamental command to understand any CLI tool is to ask for help. This will list all available commands and general usage information.

    ```bash
    opencode --help
    ```

    **Expected Output (Example):**

    ```
    Usage: opencode [command] [options]

    Commands:
      read <filePath>        Read a file or directory from the local filesystem
      write <filePath>       Write a file to the local filesystem
      edit <filePath>        Performs exact string replacements in files
      bash <command>         Executes a given bash command
      ...

    Options:
      --version  Show version number
      --help     Show help
    ```

2.  **Explore the Current Directory:**

    OpenCode has a `bash` tool that allows it to execute arbitrary shell commands. Let's use it to list the contents of your current directory.

    ```bash
    opencode bash --command "ls -F"
    ```

    *Note: OpenCode often provides a description for its `bash` commands. If you were to type this directly into OpenCode, it might generate a description for you.*

    **Expected Output (Example, will vary based on your directory):**

    ```
    .github/
    README.md
    docs/
    examples/
    ... (other files/directories)
    ```

This brief interaction demonstrates OpenCode's ability to understand commands and execute them within your environment. In the next section, we'll dive deeper into the core concepts and tools that power OpenCode.
