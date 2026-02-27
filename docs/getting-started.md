# Getting Started with GitHub Copilot (Codex)

GitHub Copilot is an AI pair programmer powered by OpenAI Codex. It helps you write code faster and with less work by offering autocomplete-style suggestions and interactive chat features.

## Prerequisites
To use GitHub Copilot, you must have an active GitHub Copilot subscription (Individual, Business, or Enterprise).

## Installation

GitHub Copilot is available as an extension for a variety of popular IDEs:
*   Visual Studio Code
*   Visual Studio
*   JetBrains IDEs (IntelliJ, PyCharm, WebStorm, etc.)
*   Neovim
*   Azure Data Studio

### Visual Studio Code Setup
1. Open the Extensions view (`Ctrl+Shift+X` or `Cmd+Shift+X`).
2. Search for **GitHub Copilot**.
3. Install both the **GitHub Copilot** extension and the **GitHub Copilot Chat** extension.
4. Once installed, a toast notification will prompt you to sign in to GitHub.
5. Follow the authentication prompts in your browser.

### JetBrains IDEs Setup (IntelliJ, PyCharm, etc.)
1. Go to **File > Settings** (or **Preferences** on macOS), then select **Plugins**.
2. Click the **Marketplace** tab and search for **GitHub Copilot**.
3. Click **Install**. Wait for the installation to finish, and click **Restart IDE**.
4. After restarting, click the Copilot icon in the status bar and log in to GitHub.

### Visual Studio (Windows) Setup
1. Open Visual Studio and go to **Extensions > Manage Extensions**.
2. Search and download **GitHub Copilot** from the Online section.
3. Close Visual Studio to trigger the VSIX installer. Allow the installation to complete.
4. Re-open Visual Studio and sign in to your GitHub account when prompted.

> [!NOTE]
> Copilot Business and Enterprise users can explicitly toggle Codex and Claude models on or off via their organizational settings on GitHub.com.

## First Interaction
Open a file and start typing a comment describing what you want:
```javascript
// Function to calculate the difference in days between two dates
function
```
As you type, Copilot will suggest the rest of the function in gray text (Ghost Text). Press `Tab` to accept the suggestion.
