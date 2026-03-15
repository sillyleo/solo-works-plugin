---
description: Set up Solo Works API access. Use when authentication fails, the user hasn't configured their API key, or asks how to get started with Solo Works.
---

# Solo Works Setup

Help the user configure their Solo Works API key for AI image editing.

## Steps

1. **Check if already configured:** Try calling `list_workflows`. If it succeeds, tell the user they're already set up and ask what they'd like to edit.

2. **If auth fails, guide setup:**

   a. "To use Solo Works AI image editing, you need an API key. Here's how to get one:"

   b. **Register:** "Go to https://soloworks.app/auth/register to create an account (if you don't have one)."

   c. **Get API Key:** "Go to https://soloworks.app/api-keys and click 'Create API Key'. Copy the key that starts with `sk_live_`."

   d. **Set environment variable:** "Set the API key as an environment variable:
      ```
      export SOLO_WORKS_API_KEY=sk_live_your_key_here
      ```
      Add this to your shell profile (~/.zshrc or ~/.bashrc) to persist it."

   e. **Restart Claude Code** after setting the env var.

3. **Verify:** Call `list_workflows` to confirm the connection works. If successful, show the available workflows.

4. **Credits:** "New accounts get 20 free credits. You can purchase more at https://soloworks.app/buy"

## Important
- The API key format is `sk_live_` followed by a random string
- All Solo Works tools require authentication — nothing works without a valid key
- If the key is invalid or expired, guide the user to generate a new one
