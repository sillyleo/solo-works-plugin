---
name: edit-image
description: "Edit images using Solo Works AI workflows — background removal, model replacement, style transfer, lighting adjustment, product photos, and more."
user-invocable: true
argument-hint: [describe what edit you want]
---

# AI Image Editing with Solo Works

You have access to Solo Works MCP tools for AI image editing. Follow this workflow to help users edit their images.

## Available Tools

| Tool | Purpose |
|------|---------|
| `list_workflows` | List all available editing operations |
| `get_workflow_inputs` | Get required inputs for a specific workflow |
| `execute_workflow` | Execute a workflow with user's image |
| `get_execution_status` | Poll for execution results |
| `get_credits_balance` | Check user's credit balance |

## Workflow

### Step 1: Discover workflows
Call `list_workflows` to see available operations. You can filter by tag (e.g., "fashion", "product").

Present the results to the user in a clear list showing:
- Workflow name and description
- Credit cost (min-max range)
- Tags

### Step 2: Get input requirements
Once the user picks a workflow, call `get_workflow_inputs` with the `workflowId`.

This returns:
- **imageFields**: What images are needed (usually one primary image)
- **textFields**: Text inputs. Some have `presetOptions` — if so, show the user the available options and use the `optionId` (not the label) when executing.
- **switchFields**: Toggle options between modes

### Step 3: Collect inputs
Ask the user for:
- Their image (URL or file path)
- Any required text inputs
- Any switch selections
- Optional: aspect ratio and image size preferences

### Step 4: Execute
Call `execute_workflow` with:
- `workflowId`: The chosen workflow ID
- `image`: Pass as `{"download_url": "<image_url>", "file_id": "claude-upload"}` — the server accepts OpenAI file object format
- `texts`: Object mapping fieldId to value (use optionId for preset fields)
- `switchSelections`: Object mapping switchFieldId to optionId (if applicable)
- `aspectRatio`: Optional ("auto", "1:1", "2:3", "3:2", "3:4", "4:3", "4:5", "5:4", "9:16", "16:9", "21:9")
- `imageSize`: Optional ("1K" or "2K")

**Important:** Tell the user the credit cost BEFORE executing.

### Step 5: Poll for results
After `execute_workflow` returns an `executionId`, poll `get_execution_status` every 5 seconds.

- **running**: Show progress percentage, keep polling
- **completed**: Show the result image URLs (jpgUrl and pngUrl)
- **failed**: Show the error message and suggest retry

**Timeout:** Stop polling after 5 minutes. Provide the executionId so the user can check later.

### Step 6: Present results
When completed, show:
- The JPG result URL (preferred for display)
- The PNG result URL (for higher quality download)
- Credits consumed

## Edge Cases

- **Auth error**: Guide user to run the setup skill (`/solo-works:setup`)
- **Insufficient credits**: Show balance and link to https://soloworks.app/buy
- **Server unreachable**: Inform user to check https://soloworks.app status
- **Multiple images**: Explain each image costs credits separately

## Tips
- Always check available workflows first — new workflows may be added server-side at any time
- For text fields with presets, always use the `optionId`, never the display label
- Result image URLs are temporary signed URLs — suggest the user download/save them
- Credit costs vary: most workflows cost 1-2 credits, complex ones (3D transform) cost up to 8
