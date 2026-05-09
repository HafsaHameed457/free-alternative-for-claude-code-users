# 04-common-workflows.md

OpenCode shines when applied to common software engineering workflows. This section provides practical guidance and examples on how to use OpenCode for tasks you encounter daily.

## 1. Understanding a Codebase

Before making changes, it's crucial to understand the existing codebase. OpenCode offers powerful tools for exploration.

**Scenario:** You've just joined a new project and need to find all `.js` files in the `src` directory and then locate all functions defined within `auth.js`.

1.  **Find all `.js` files in `src/` using `glob`:**

    ```bash
    opencode glob --pattern "src/**/*.js"
    ```

    *Explanation:* This command will return a list of all JavaScript files within the `src` directory and its subdirectories.

2.  **Read the content of a specific file (e.g., `src/auth.js`):**

    (Assuming `src/auth.js` was found in the previous `glob` output)

    ```bash
    opencode read --filePath /path/to/your/project/src/auth.js
    ```

    *Explanation:* This will display the entire content of `auth.js`, allowing you to understand its structure and logic.

3.  **Locate function definitions within `auth.js` using `grep` (after reading the file):**

    ```bash
    opencode grep --pattern "function\s+\w+\s*\(" --include "auth.js" --path /path/to/your/project/src/
    ```

    *Explanation:* This regex pattern looks for the keyword `function` followed by a word (the function name) and an opening parenthesis, effectively finding function definitions. The `include` parameter narrows the search to `auth.js`.

## 2. Making Small Code Changes

OpenCode is excellent for precise, small modifications.

**Scenario:** You need to fix a typo in a comment in `config.py`.

1.  **Read `config.py` to identify the typo:**

    ```bash
    opencode read --filePath /path/to/your/project/config.py
    ```

    *Example Content of `config.py`:*
    ```python
    # This is a important configuration file.
    DB_HOST = "localhost"
    ```

2.  **Use `edit` to correct the typo:**

    ```bash
    opencode edit --filePath /path/to/your/project/config.py --oldString "# This is a important configuration file." --newString "# This is an important configuration file."
    ```

    *Explanation:* The `edit` tool performs an exact string replacement. Providing the full line as `oldString` ensures precision.

## 3. Refactoring Code

For more substantial changes, like renaming a function across multiple files, OpenCode can automate the process.

**Scenario:** You want to rename a function `getUserData` to `fetchUserProfile` across your project.

1.  **Grep for all occurrences of `getUserData`:**

    ```bash
    opencode grep --pattern "getUserData" --include "*.js,*.ts,*.py"
    ```

    *Explanation:* This helps you understand the scope of the change. OpenCode will return file paths and line numbers where `getUserData` is found.

2.  **For each file identified, use `edit` with `replaceAll` (or iteratively):**

    (Let's assume `src/api.js` and `src/components/UserDisplay.js` were found)

    ```bash
    opencode edit --filePath /path/to/your/project/src/api.js --oldString "getUserData" --newString "fetchUserProfile" --replaceAll true
    ```

    ```bash
    opencode edit --filePath /path/to/your/project/src/components/UserDisplay.js --oldString "getUserData" --newString "fetchUserProfile" --replaceAll true
    ```

    *Explanation:* `replaceAll: true` is crucial here to ensure all instances of the function name are updated within each file.

3.  **Run tests to verify the refactor (covered in section 5).

## 4. Debugging Applications

OpenCode can help you run debug commands and analyze output.

**Scenario:** Your Python application is throwing an error, and you need to run tests and inspect logs.

1.  **Run the project's test suite:**

    ```bash
    opencode bash --command "pytest tests/" --description "Run all Python tests"
    ```

    *Explanation:* This executes your test runner. OpenCode will capture and display the output, including any failures.

2.  **Inspect a log file (e.g., `app.log`):**

    ```bash
    opencode read --filePath /path/to/your/project/app.log
    ```

    *Explanation:* You can quickly review recent log entries for error messages or unusual activity.

## 5. Implementing New Features

For larger tasks, OpenCode can guide you through the process, from scaffolding to integration.

**Scenario:** Add a new `ContactForm` component to a React application.

1.  **Create the new component file:**

    ```bash
    opencode write --filePath /path/to/your/project/src/components/ContactForm.js --content "// React ContactForm component code here"
    ```

    *Explanation:* OpenCode creates the new file with placeholder content.

2.  **Edit `App.js` to import and render the new component:**

    (First, `read` `App.js` to get its current content, then `edit`.)

    ```bash
    opencode edit --filePath /path/to/your/project/src/App.js --oldString "function App() {" --newString "import ContactForm from './components/ContactForm';\n\nfunction App() {" --replaceAll false
    ```
    ```bash
    opencode edit --filePath /path/to/your/project/src/App.js --oldString "<header className=\"App-header\">" --newString "<header className=\"App-header\">\n        <ContactForm />" --replaceAll false
    ```

    *Explanation:* These `edit` commands add the import statement and integrate the new component into the main application. You might need to adjust the `oldString` to ensure uniqueness.

3.  **Add styling to `App.css` (if needed):**

    ```bash
    opencode edit --filePath /path/to/your/project/src/App.css --oldString "/* existing css */" --newString "/* existing css */\n\n.contact-form { /* new styles */ }" --replaceAll false
    ```

## 6. Testing and Verification

After making changes, it's crucial to verify their correctness.

**Scenario:** You've implemented a new feature and need to run the project's test suite and linting tools.

1.  **Identify the correct test command:** Look at `package.json` (for Node.js projects), `pom.xml` (for Maven), `build.gradle` (for Gradle), or project documentation for common `test` or `build` scripts.

    ```bash
    opencode read --filePath /path/to/your/project/package.json
    ```

    *Example `package.json` `scripts` section:*
    ```json
    "scripts": {
        "start": "react-scripts start",
        "build": "react-scripts build",
        "test": "react-scripts test",
        "lint": "eslint ."
    },
    ```

2.  **Run tests:**

    ```bash
    opencode bash --command "npm test" --description "Run project unit tests"
    ```

3.  **Run linter/type checker:**

    ```bash
    opencode bash --command "npm run lint" --description "Run code linter"
    ```

    *Explanation:* OpenCode will execute these commands and display their output. You can then address any reported errors or warnings.

## 7. Version Control with Git

OpenCode can assist with common Git operations, but remember that the `bash` tool provides direct access to Git.

**Scenario:** You've made some changes and want to commit them.

1.  **Check current Git status:**

    ```bash
    opencode bash --command "git status" --description "Show current Git status"
    ```

    *Explanation:* This shows modified, staged, and untracked files.

2.  **Stage your changes:**

    ```bash
    opencode bash --command "git add ." --description "Stage all changes"
    ```

3.  **Commit your changes:**

    ```bash
    opencode bash --command "git commit -m \"feat: add new contact form\"" --description "Commit changes with a message"
    ```

    *Explanation:* Remember to use proper commit message conventions for your project. Note the escaped quotes for the commit message.

These examples illustrate the versatility of OpenCode across various development tasks. By combining its core tools, you can automate many aspects of your workflow and focus on more complex problem-solving.
