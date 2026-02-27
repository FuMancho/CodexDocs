# GitHub Copilot Integrations & Enterprise Features

GitHub Copilot extends beyond the local IDE when using Copilot Business or Copilot Enterprise, deeply integrating into the broader development lifecycle.

## Copilot in the CLI
GitHub Copilot in the CLI (`gh copilot`) brings the pair programmer to your terminal. It helps you remember shell commands or explain what a command does before you run it.

### Installation
You must have the GitHub CLI installed. Then run:
```bash
gh extension install github/gh-copilot
```

### Usage
*   `gh copilot suggest "find all javascript files updated in the last 2 days"`: Generates the shell command based on natural language.
*   `gh copilot explain "chmod 755 script.sh"`: Explains what a specific shell command does.

## Copilot for Pull Requests
If your organization has Copilot Enterprise, Copilot can assist with Code Review on GitHub.com.

*   **PR Summaries:** Copilot can automatically generate a high-level summary of the changes in a PR description, making it easier for reviewers to understand the context.
*   **Review Assistance:** It can highlight potential bugs or security flaws in the PR diff directly in the GitHub web UI.

## Organizational Policy Management
Administrators can configure Copilot behavior across the organization:
*   **Public Code Match:** Admins can enable or disable Copilot's ability to suggest code that matches public code on GitHub.
*   **Telemetry:** Control what telemetry data is sent back to GitHub.
*   **Content Exclusion:** Define repository-wide rules (like `.copilotignore` or via the web UI) to ensure Copilot never reads or suggests code within sensitive directories. This is critical for maintaining compliance on proprietary algorithms or credential files.

## Integrating with Custom Models
GitHub is increasingly allowing enterprise customers to fine-tune Copilot on their own proprietary codebases, ensuring the suggestions closely follow internal style guides and utilize internal monolithic libraries accurately.
