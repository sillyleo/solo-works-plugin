# Solo Works — Claude Plugin

AI image editing directly in Claude. Remove backgrounds, replace models, transfer styles, adjust lighting, generate product photos, and more.

Powered by [Solo Works](https://soloworks.app) AI platform.

## Quick Start

### 1. Install the plugin

Add marketplace from GitHub in Claude Desktop: `sillyleo/solo-works-plugin`

Or from Claude Code CLI:
```bash
claude plugin install solo-works@solo-works-marketplace
```

### 2. Connect your account

When you first use an editing tool, Claude will automatically open a browser window for you to log in to Solo Works. No API keys or terminal commands needed.

### 3. Start editing

Just ask Claude to edit your images:

> "Remove the background from this product photo"

> "Replace the model in this fashion image with a different pose"

> "Transfer the style of this reference image to my photo"

## Available Skills

| Skill | Command | Description |
|-------|---------|-------------|
| Edit Image | `/solo-works:edit-image` | Full image editing workflow |
| Check Credits | `/solo-works:check-credits` | View your credit balance |
| Setup | `/solo-works:setup` | Connection help |

## How It Works

1. Claude discovers available AI editing workflows from Solo Works
2. You choose what you want to do and provide your image
3. Solo Works processes your image using Gemini AI
4. You get back the edited image (JPG + PNG)

Each operation costs 1-8 credits depending on complexity. New accounts get **20 free credits**.

## Credits & Pricing

- **Free credits:** 20 on sign-up
- **Purchase:** 20 credits for $3.65 USD
- **Buy more:** [soloworks.app/buy](https://soloworks.app/buy)

| Operation | Credits |
|-----------|---------|
| Background removal | 1 |
| Model replacement | 1-2 |
| Style transfer | 1 |
| Lighting adjustment | 1 |
| Product photo generation | 1-2 |
| 3D model generation | 8 |

## Troubleshooting

**"Authentication required" error:**
Run `/solo-works:setup` for connection help.

**"Insufficient credits" error:**
Purchase more credits at [soloworks.app/buy](https://soloworks.app/buy).

## Links

- [Solo Works Platform](https://soloworks.app)
- [Buy Credits](https://soloworks.app/buy)

## License

MIT
