# Solo Works — Claude Plugin

AI image editing directly in Claude. Remove backgrounds, replace models, transfer styles, adjust lighting, generate product photos, and more.

Powered by [Solo Works](https://soloworks.app) AI platform.

## Quick Start

### 1. Install the plugin

From Claude Code:
```bash
claude plugin install github:sillyleo/solo-works-plugin
```

Or browse plugins in Claude Desktop Cowork and search for "Solo Works".

### 2. Get your API key

1. Create an account at [soloworks.app/auth/register](https://soloworks.app/auth/register)
2. Go to [soloworks.app/api-keys](https://soloworks.app/api-keys)
3. Click **Create API Key** and copy the key (starts with `sk_live_`)

### 3. Set your API key

```bash
export SOLO_WORKS_API_KEY=sk_live_your_key_here
```

Add this to your `~/.zshrc` or `~/.bashrc` to persist it, then restart Claude.

### 4. Start editing

Just ask Claude to edit your images:

> "Remove the background from this product photo: https://example.com/photo.jpg"

> "Replace the model in this fashion image with a different pose"

> "Transfer the style of this reference image to my photo"

## Available Skills

| Skill | Command | Description |
|-------|---------|-------------|
| Edit Image | `/solo-works:edit-image` | Full image editing workflow |
| Check Credits | `/solo-works:check-credits` | View your credit balance |
| Setup | `/solo-works:setup` | Configure API key |

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
Run `/solo-works:setup` or check that `SOLO_WORKS_API_KEY` is set in your environment.

**"Insufficient credits" error:**
Purchase more credits at [soloworks.app/buy](https://soloworks.app/buy).

**Tool calls failing:**
Make sure you've restarted Claude after setting the API key.

## Links

- [Solo Works Platform](https://soloworks.app)
- [API Key Management](https://soloworks.app/api-keys)
- [Buy Credits](https://soloworks.app/buy)

## License

MIT
