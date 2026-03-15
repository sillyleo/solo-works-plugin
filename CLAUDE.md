# Solo Works — AI Image Editing Plugin

This plugin connects Claude to Solo Works' AI image editing platform via MCP.

## Available MCP Tools

All tools require authentication via `SOLO_WORKS_API_KEY` env var.

| Tool | Purpose |
|------|---------|
| `list_workflows` | List available AI editing workflows (filter by tag) |
| `get_workflow_inputs` | Get input schema for a workflow (image/text/switch fields) |
| `execute_workflow` | Execute a workflow, returns executionId |
| `get_execution_status` | Poll execution status and results |
| `get_credits_balance` | Check credit balance |

## Key Behaviors

- **Image format:** `execute_workflow` expects image as `{"download_url": "<url>", "file_id": "claude-upload"}`
- **Polling:** After execution, poll `get_execution_status` every 5 seconds. Timeout after 5 minutes.
- **Credits:** Always inform users of credit cost before executing. Most workflows: 1-2 credits. Max: 8.
- **Presets:** For text fields with `presetOptions`, always use `optionId` (not the label text).
- **Results:** Images returned as temporary signed URLs (JPG + PNG). Suggest users save them.
- **Auth errors:** Guide to `/solo-works:setup` skill.
- **Low credits:** Link to https://soloworks.app/buy

## Links

- Register: https://soloworks.app/auth/register
- API Keys: https://soloworks.app/api-keys
- Buy Credits: https://soloworks.app/buy
- Homepage: https://soloworks.app
