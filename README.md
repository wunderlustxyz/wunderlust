# Wunderlust

Hand-picked creative cards for your AI agent: award-winning sites, motion and animation libraries, 3D and WebGL tools, UI components, inspiration galleries, AI tools and coding skills. Every card is written up by hand, with the one idea worth exploring in it, its caveats and the official link.

This plugin adds two things to Claude Code and Codex:

- **The Wunderlust connector** (`https://wunderlust.xyz/api/mcp`): search the stash, read a card, find similar ones, get a random selection, show chosen cards in the chat, list the categories and patterns, and read a shared collection. Read-only, no account, no key.
- **The `wunderlust-references` skill**: tells your agent when to look in Wunderlust and how to present what it finds.

## Install

### Claude Code

```
/plugin marketplace add wunderlustxyz/wunderlust
/plugin install wunderlust@wunderlust
```

Then restart Claude Code (or run `/reload-plugins`) and ask: *"Find award-winning sites with scroll-driven storytelling."*

### Codex

```
codex plugin marketplace add wunderlustxyz/wunderlust
codex plugin add wunderlust@wunderlust
```

Then start a new Codex session and ask: *"Which React animation library should I use for page transitions?"* You can also install it from Plugins in the ChatGPT desktop app.

### From a terminal, for both

```
claude plugin marketplace add wunderlustxyz/wunderlust && claude plugin install wunderlust@wunderlust
codex plugin marketplace add wunderlustxyz/wunderlust && codex plugin add wunderlust@wunderlust
```

### Any other AI app

Add `https://wunderlust.xyz/api/mcp` as a remote MCP server (Streamable HTTP, no auth). Step-by-step guides for Claude, ChatGPT, Cursor, VS Code and more: [https://wunderlust.xyz/connect](https://wunderlust.xyz/connect).

## Tools

| Tool | What it does |
|---|---|
| `search_references` | Search by free text or by category, tag, pattern or editorial pick |
| `get_references` | Full write-up of up to 20 cards by id. Design cards also say why the idea works and what to watch out for |
| `similar_references` | Cards similar to one you name |
| `random_references` | A random selection, for open-ended inspiration |
| `show_references` | Shows chosen cards in the chat with cover and preview video (apps that support it) |
| `list_facets` | The valid categories, tags, patterns and picks |
| `get_collection` | A collection someone shared from Wunderlust |

All tools are read-only. Fair use: up to 600 requests per hour per network.

## Links

- Website: https://wunderlust.xyz
- Docs: https://wunderlust.xyz/connect
- Privacy: https://wunderlust.xyz/privacy
- Terms: https://wunderlust.xyz/terms
- Support: hello@wunderlust.xyz

## License

MIT for the files in this repository. The sites, skills and tools in the cards belong to their makers.
