# Session 7: Connecting to Design Tools (MCP)

**Duration:** 45 minutes
**Problem:** Design tools and code tools don't talk to each other
**Solution:** MCP (Model Context Protocol) bridges Claude Code to FigJam
**Output:** Claude drawing on a shared FigJam board in real time

---

## The Problem

You've got Claude Code building your app. You've got FigJam for brainstorming, sitemaps, retros. But they're separate worlds. You copy-paste between them. You screenshot. You describe what you're looking at.

What if Claude could just look at the board? Or draw on it?

That's what MCP does. It gives Claude Code hands in other tools.

---

## The Solution

**MCP** is a protocol that lets Claude Code talk to external tools through a standardized interface. Think of it like USB for AI — plug in a tool, Claude can use it.

We'll connect Claude Code to FigJam using a community MCP server that runs locally on your machine. No paid plans. No rate limits. Claude reads your board, creates shapes, draws connectors, deletes nodes — all from the terminal.

---

## Structure

### Part 1: What is MCP? (5 min)

**Explain the concept before touching any tools:**

> "MCP stands for Model Context Protocol. It's how Claude Code connects to things outside your codebase — Figma, Google Calendar, databases, Slack, anything with an MCP server.
>
> Think of it this way: Claude Code can already read and write files. MCP gives it the same ability in other tools. Today we're connecting it to FigJam."

**Show the architecture on a whiteboard:**

```
Claude Code  →  MCP Server  →  WebSocket  →  Figma Plugin  →  FigJam Board
 (terminal)     (local)       (port 3055)    (Desktop app)     (your board)
```

> "Everything runs locally. Nothing leaves your machine except the normal Figma connection."

---

### Part 2: Setup (15 min)

**Walk through the setup together. Everyone follows along.**

**Step 1: Install Bun**

> "Bun is a JavaScript runtime — like Node.js but faster. We need it to run the WebSocket bridge. It's temporary — we'll show you how to uninstall it at the end."

```bash
curl -fsSL https://bun.sh/install | bash
```

Check it worked:
```bash
~/.bun/bin/bun --version
```

**Check-in:** "Raise your hand when you see a version number."

**Step 2: Install the community MCP server**

> "There's an official Figma MCP, but it limits you to 6 calls per month on a free plan. We burned through that in 15 minutes when we tested it. So we use the community version — unlimited, open source, no tracking."

```bash
git clone https://github.com/arinspunk/claude-talk-to-figma-mcp.git ~/.local/share/claude-talk-to-figma-mcp
cd ~/.local/share/claude-talk-to-figma-mcp && ~/.bun/bin/bun install && ~/.bun/bin/bun run build
```

**Step 3: Register it with Claude Code**

```bash
claude mcp add -s user figma-community -- ~/.bun/bin/bun run ~/.local/share/claude-talk-to-figma-mcp/dist/talk_to_figma_mcp/server.js
```

**Step 4: Install the Figma plugin**

1. Open Figma Desktop
2. Go to **Plugins > Development > Import plugin from manifest**
3. Navigate to `~/.local/share/claude-talk-to-figma-mcp/src/claude_mcp_plugin/manifest.json`

> "Can't see the `.local` folder? Press Cmd+Shift+. to show hidden folders."

**Check-in:** "Raise your hand when you've imported the plugin."

---

### Part 3: Draw a Circle (10 min)

**This is the "hello world" moment.**

**Start the WebSocket relay** (in a separate terminal):
```bash
~/.bun/bin/bun run ~/.local/share/claude-talk-to-figma-mcp/dist/socket.js
```

**Open a FigJam board** in Figma Desktop.

**Run the plugin:** Right-click canvas > Plugins > Development > claude-talk-to-figma-mcp

> "You should see 'Connected on port 3055!' and a channel ID. Copy that channel ID — that's how Claude Code finds your board."

**Restart Claude Code** (needed the first time so it loads the new MCP tools).

**Tell Claude:**

> "Connect to Figma channel [paste-channel-id] and draw a purple circle on the board"

**Watch it happen in real time on the FigJam board.**

> "That's it. Claude can now see and draw on your board. No screenshots. No copy-paste. Direct connection."

**Check-in:** "Raise your hand when you see the circle on your board."

**If someone's circle doesn't appear:**
- Is the socket server terminal still running?
- Did they restart Claude Code?
- Is the channel ID correct? It changes every time the plugin reconnects.

---

### Part 4: Build Something Real (15 min)

**Now that the connection works, do something useful.**

> "Let's have Claude draw a sitemap of the app you built in Sessions 1-4. Tell Claude what pages your app has and ask it to draw the structure on FigJam."

**Example prompt:**

> "Read my app's routes and draw a sitemap on the FigJam board. Use rounded rectangles for pages and straight connectors between them."

**Things to watch for:**

- Claude will use `create_shape_with_text` for nodes and `create_connector` for arrows
- If shapes overlap, tell Claude to use smaller shapes (120x50) with wider spacing (280px gaps)
- If connectors route sideways, tell Claude to use STRAIGHT not ELBOWED
- If something looks wrong, Claude can `delete_node` and redo it

**Let them experiment for 10 minutes.** Some will draw sitemaps. Some will create flowcharts. Some will make retro boards.

> "The point isn't the diagram. The point is that your AI assistant can now reach into your design tools. That changes how you collaborate."

---

## What They Just Learned

| Before Session 7 | After Session 7 |
|-------------------|-----------------|
| Design and code are separate | Claude draws on FigJam directly |
| Copy-paste between tools | MCP bridges tools automatically |
| MCP is abstract concept | Installed and used a real MCP |
| One tool at a time | Tools connected through protocols |

---

## Success Criteria

By the end of Session 7:

- [ ] Everyone has Bun installed and the community MCP server running
- [ ] Everyone has connected Claude Code to a FigJam board
- [ ] Everyone has seen Claude create at least one shape on their board
- [ ] Everyone understands what MCP is and why it matters

---

## Facilitator Notes

**This session is about expanding the mental model.**

Sessions 1-6 taught them to work with AI inside the codebase. Session 7 shows that AI can reach into other tools. MCP is the "and also" moment — Protocol files give AI memory, MCP gives AI hands.

**Why the community MCP and not the official one:**

The official Figma MCP (`claude plugin install figma@claude-plugins-official`) works but gives you 6 read calls per month on the free plan. We burned through all 6 in a single session building a sitemap. The community version has no limits and runs entirely locally.

**Common issues:**

- "Bun won't install" → Check internet connection. If blocked by corporate firewall, have a USB drive with the Bun binary ready.
- "Plugin doesn't show in Figma" → Must use Figma Desktop, not browser. Must import via Development > Import from manifest.
- "Channel ID doesn't work" → Channel IDs change every time the plugin reconnects. Get a fresh one.
- "Claude's tools aren't showing" → Must restart Claude Code after registering a new MCP for the first time. Tools load on session start.
- "Connection keeps dropping" → Don't fire more than ~15 parallel calls. If it drops, re-open the plugin and get a new channel ID.
- "Shapes are overlapping" → Tell Claude to use smaller shapes and wider spacing. 120x50 with 280px gaps works well.

**Cleanup at end of session:**

```bash
# Kill the WebSocket relay
pkill -f "socket.js"
```

If participants want to remove everything after the workshop:

```bash
claude mcp remove figma-community -s user
rm -rf ~/.local/share/claude-talk-to-figma-mcp
rm -rf ~/.bun
# Edit ~/.zshrc and remove the line containing ".bun/bin"
```

**Energy goal:**

End this session with: "AI can reach into my other tools. What else could I connect?"
