# Features of GitHub Copilot & Codex

GitHub Copilot provides two primary modes of interaction: Ghost Text (inline suggestions) and Copilot Chat.

## Ghost Text (Inline Completions)
This is the core autocomplete functionality that GitHub Copilot was built on.
When you type code or write a natural language comment, Copilot uses the context of your current file and related open files to predict the next lines of code.

### Prompt Engineering for Ghost Text
To get the best suggestions, craft clear prompt comments:
1. **Start General, Get Specific:** Give high-level instructions, then break it down into steps.
2. **Give Examples:** Provide an example of the input and expected output in the comment.
3. **Be Specific:** Say exactly what libraries or approaches you want it to use.

> [!TIP]
> If a suggestion isn't quite right, you don't use the mouse! Keep typing part of the solution you want to steer the model, and the Ghost Text will dynamically recalculate.

## Copilot Chat
Copilot Chat provides a conversational interface within your IDE, acting as a pair programmer. You can ask it to:
*   Generate unit tests for a specific function.
*   Find bugs in the highlighted code snippet.
*   Explain an unfamiliar codebase.
*   Propose a structural refactor.

### Context Awareness
GitHub Copilot uses multiple techniques to understand your intent:
1.  **Cursor Position:** The most heavily weighted context is what is directly above and below your cursor.
2.  **Open Tabs:** Copilot scans the contents of other files currently open in your IDE. To improve suggestions, keep relevant files (like interfaces, types, and utility functions) open in tabs.
3.  **Path and Filename:** Copilot uses the name of the file and its path to determine the language and framework conventions.

### Slash Commands and Variables
Inside the chat, you can use specialized slash commands and variables to route context efficiently.
*   `/explain`: Ask Copilot to explain code.
*   `/tests`: Scaffold unit tests.
*   `@workspace`: Provide Copilot with context from the entire open repository.
*   `#file`: Explicitly include a specific file in the prompt context.

## Privacy Settings
If you are working on sensitive internal files, you can use `.copilotignore` rules or organization-level content exclusion (if using a Business/Enterprise plan) to ensure Copilot never reads or suggests code within certain directories.
