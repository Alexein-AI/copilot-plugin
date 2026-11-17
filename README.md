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

## Recall and saving sessions (optional API key)

The plugin also adds hooks for GitHub Copilot CLI and VS Code (`com.github.copilot/hooks/hooks.json`; Kiro ignores them). Without an API key they only add a note on how to use the memory tools at the start of each session; nothing is read or sent.

With a key in `ALEXEIN_API_KEY` (a personal key from **My memory › Keys** in the Alexein app, **Read and write**;
or `api_key` in `~/.config/alexein/hooks.json`):

- **Recall.** The first message of each session is looked up in your memory and the best matches are added as
  context, with the first tool the agent runs (Copilot's prompt hook can't add context). One search per session.
- **Saving sessions.** What you ask and the agent's final replies are saved to your memory, with the names of files
  changed and commands run (never their contents or output), five exchanges at a time. Anything that looks like a
  password, key or token is removed first. `ALEXEIN_CAPTURE=false` keeps recall and saves nothing.

`python3 <plugin>/scripts/alexein_hooks.py run copilot pause` (or `resume`, `status`) turns this off and on. The
hooks need `python3`; they are the same script as the Claude Code plugin's
([claude-plugins](https://github.com/Alexein-AI/claude-plugins)).
