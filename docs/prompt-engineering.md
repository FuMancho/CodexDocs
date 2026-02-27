# Prompt Engineering for GitHub Copilot

Writing effective prompts (comments) for Copilot is an acquired skill. Follow these techniques to steer Codex toward exactly the implementation you want.

## Comment-Driven Development
Treat Copilot like an extremely junior developer. You write the specification in English, and Copilot types the implementation.

**Example workflow:**
```python
# Create a Flask app
# Add a route for /health that returns a 200 JSON OK status
# Add a route for /users that queries the SQLite database for all rows in the users table and returns them as JSON
```
By writing all these comments at once, Copilot understands the full scope and will begin generating the boilerplate line-by-line as you press `Tab` and `Enter`.

## Best Practices

### 1. Give Context Before Action
Don't just ask for an action out of context. Define the setup first.
*   **Poor:** `// sort the list`
*   **Better:** `// Given an array of User objects, sort them by the 'last_login' property in descending order.`

### 2. Provide Examples of Expected Behavior
If you need a specific data transformation, show Copilot what the input and output look like in the comments.
```javascript
/*
 * Function: slugifyTitle
 * Example Input: "Hello World 2024!"
 * Example Output: "hello-world-2024"
 */
function slugifyTitle(title) {
```

### 3. Open Relevant Files
Because Copilot uses "Neighboring Tabs" as context, always open the files that contain the classes, types, or utility functions you want it to use. If you are writing a React component, open the `Button.jsx` and `api.js` files in other tabs so Copilot knows their signatures.

### 4. Nudge the Model
If Copilot suggests something totally wrong, don't delete the comment—nudge the code directly. Type the first few characters of the variable or class you *want* it to use, and let it recalculate.

## Avoiding Anti-Patterns
*   **Do not trust generated API keys or URLs**: Copilot may hallucinate endpoints or credentials based on open-source repositories.
*   **Review all logic:** Copilot might use deprecated libraries or skip edge cases if they weren't explicitly called out in your prompt.
