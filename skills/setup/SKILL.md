---
name: setup
description: "Set up Solo Works connection. Use when authentication fails or the MCP server isn't connected."
user-invocable: true
---

# Solo Works Setup

Help the user connect their Solo Works account for AI image editing.

## Steps

1. **Check if already connected:** Try calling `list_workflows`. If it succeeds, tell the user they're already set up and ask what they'd like to edit.

2. **If not connected:**

   a. "Solo Works connects automatically via OAuth. When you first try to use an editing tool, a browser window should open for you to log in."

   b. "If the browser didn't open, try using the `/solo-works:edit-image` skill — it should trigger the connection flow."

   c. "If you don't have an account yet, you can register at https://soloworks.app/auth/register"

3. **Verify:** Call `list_workflows` to confirm the connection works. If successful, show the available workflows.

4. **Credits:** "New accounts get 20 free credits. You can purchase more at https://soloworks.app/buy"

## Important
- Authentication is handled automatically via OAuth — no API keys or terminal commands needed
- If the connection fails, suggest the user restart Claude Desktop and try again
- All Solo Works tools require authentication — the OAuth flow must complete first
