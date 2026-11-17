# Alexein AI for GitHub Copilot and Kiro

Gives your coding agent your [Alexein](https://alexein.ai) memory: it searches what you have told Alexein before
answering, and saves new facts as you work, so the next session, and your other apps, pick up where this one left off.

The plugin adds one MCP server, `alexein-ai`, at `https://api.alexein.ai/v1/mcp` (Streamable HTTP), and a short
skill, `alexein-memory`, that tells the agent when to search and when to save. The full tool list is at
[docs.alexein.ai/mcp/tools](https://docs.alexein.ai/mcp/tools).

## Install

### GitHub Copilot CLI

```
copilot plugin marketplace add Alexein-AI/copilot-plugin
copilot plugin install alexein-ai@alexein-ai
```

### VS Code

[Install in VS Code](https://vscode.dev/redirect?url=vscode%3A%2F%2Fchat-plugin%2Finstall%3Fsource%3DAlexein-AI%252Fcopilot-plugin%26plugin%3Dalexein-ai)

Or open the Command Palette, run **Chat: Install Plugin from Source**, and enter `Alexein-AI/copilot-plugin`.

### Kiro

[Add to Kiro](https://kiro.dev/launch/mcp/add?name=alexein-ai&config=%7B%22url%22%3A%22https%3A%2F%2Fapi.alexein.ai%2Fv1%2Fmcp%22%7D)

## Sign in

The first time the agent connects to Alexein, it opens Alexein's sign-in in your browser. Sign in (or create a free
account at [memory.alexein.ai](https://memory.alexein.ai)), choose what the agent may do (read only, or read and
save), and select **Allow**. No API key is needed: the server uses OAuth 2.1 with dynamic client registration.

Everything saved can be seen, downloaded and erased in the Alexein app, under **My memory**. To disconnect, uninstall
the plugin, or disconnect the app in Alexein under **AI assistants**.

## Help

[docs.alexein.ai](https://docs.alexein.ai) · zainali@alexein.ai · [Privacy](https://alexein.ai/legal/privacy) ·
[Terms](https://alexein.ai/legal/terms)
