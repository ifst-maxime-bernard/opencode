# OpenCode Environment Variables

Add the following to your fish config (`~/.config/fish/config.fish`):

```bash
# Zoho MCP server URL (includes API key in query string)
set -gx ZOHO_MCP_URL "<ZOHO_URL>"

# Context7 API key
set -gx CONTEXT7_API_KEY "<API_KEY>"
```

After adding these, reload your config:
```bash
source ~/.config/fish/config.fish
```

> **Security note**: These values were previously hardcoded in `opencode.json`.
> Keep them in your fish config (which should NOT be committed to Git) instead.
> Consider rotating the Context7 API key since it was stored in a config file.
