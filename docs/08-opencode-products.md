# OpenCode Products: Zen, Go, and Enterprise

OpenCode offers a complete product ecosystem beyond the free CLI. This guide explains each product, who it's for, and how to choose the right one for your needs.

---

## Quick Comparison

| Feature | OpenCode (Free) | Zen | Go | Enterprise |
| :--- | :--- | :--- | :--- | :--- |
| **Cost** | Free | Pay-as-you-go ($20 min) | $5/month then $10/month | Custom pricing |
| **Models** | Bring your own API key | Curated/optimized | Open-source models | Custom/Self-hosted |
| **Data Storage** | Depends on provider | US-based, zero-retention | US-based | Your infrastructure |
| **Best For** | Hobbyists, flexibility | Performance, reliability | Budget-conscious | Privacy-sensitive orgs |
| **Setup** | Add your own API | Sign up, add balance | Subscribe & start | Contact sales |

---

## OpenCode CLI (Free)

The core CLI tool is free and open source. You connect your own API keys from any LLM provider.

**Requirements:**
- Your own API key from OpenAI, Anthropic, Google, etc.
- Manual configuration in `opencode.json`

**Best when:**
- You already have API credits
- You want full control over model selection
- You're learning and experimenting

---

## Zen

Zen gives you access to a curated set of AI models that OpenCode has tested and benchmarked specifically for coding agents.

### Key Features

- **Tested models**: Only models that pass OpenCode's quality benchmarks
- **Transparent pricing**: Pay per request with zero markups
- **Auto-top up**: When balance reaches $5, auto-adds $20
- **Works everywhere**: Use with OpenCode or any other coding agent
- **Zero-retention**: Providers don't use your data for training

### Pricing

- Pay-as-you-go: Start with $20 balance
- No monthly commitment
- Auto-top up at $5 threshold

### Available Models

Zen provides curated models optimized for coding tasks. The exact models are selected and tested by OpenCode's team for consistent performance.

### When to Choose Zen

- You want the best coding performance without testing models yourself
- You prefer predictable, tested models over experimental ones
- You're willing to pay a premium for reliability

### Getting Started

1. Sign up at [opencode.ai/zen](https://opencode.ai/zen)
2. Add $20 balance (plus $1.23 processing fee)
3. Configure OpenCode to use Zen
4. Start coding with optimized models

---

## Go

OpenCode Go brings agentic coding to programmers around the world with low-cost access to capable open-source models.

### Key Features

- **Low cost**: $5 first month, then $10/month
- **Generous limits**: Up to 100x more requests than free tier
- **Reliable access**: No API key management or rate limits
- **Open-source models**: Access to curated open-source models
- **Works everywhere**: Use with OpenCode or any agent

### Pricing

- First month: $5
- Ongoing: $10/month
- Optional credit top-ups available

### Included Models

Go includes access to these open-source models:

| Model | Requests/5hr |
| :--- | :--- |
| DeepSeek V4 Flash | 31,650 |
| DeepSeek V4 Pro | 10,200 |
| Qwen3.6 Plus | 400 |
| Qwen3.5 Plus | 3,600 |
| MiniMax M2.7 | 450 |
| MiniMax M2.5 | 300 |
| MiMo-V2.5-Pro | 3,200 |
| MiMo-V2.5 | 3,000 |
| Kimi K2.6 | 290 |
| Kimi K2.5 | 150 |
| GLM-5 | 880 |
| GLM-5.1 | 200 |

### When to Choose Go

- You want affordable, predictable pricing
- You need generous usage limits
- You're new to AI coding and want a simple setup
- You prefer open-source models

### Getting Started

1. Create an account at [opencode.ai/go](https://opencode.ai/go)
2. Subscribe to Go ($5 first month)
3. Configure OpenCode to use Go
4. Start coding with reliable model access

---

## Enterprise

OpenCode Enterprise provides secure, self-hosted deployment for organizations with strict privacy requirements.

### Key Features

- **Zero data storage**: No code or context is stored
- **No ownership claims**: Your code remains yours
- **SSO integration**: Connect with your identity provider
- **Internal AI gateway**: Integrate with your existing AI infrastructure
- **Custom deployment**: Deploy on your infrastructure

### Who It's For

- Enterprise teams with strict security requirements
- Organizations with data sovereignty mandates
- Companies needing SSO/ SAML authentication
- Teams with internal AI policies

### Pricing

- Custom pricing based on organization size
- Contact OpenCode for enterprise quotes

### When to Choose Enterprise

- Your organization has strict data privacy requirements
- You need SSO or SAML integration
- You want to use internal/ private models
- Compliance requires self-hosted solutions

### Getting Started

1. Contact OpenCode through [opencode.ai/enterprise](https://opencode.ai/enterprise)
2. Discuss your organization's requirements
3. Start a trial with your team
4. Deploy across your organization

---

## How to Choose

### Decision Guide

```
Start here:
|
|  Do you have strict data privacy requirements?
|
+-- YES --> Enterprise (self-hosted)
|
+-- NO
   |
   |  What's your budget?
   |
   +-- Free (I have my own API key) --> OpenCode Free
   |
   +-- $10/month or less --> Go
   |
   +-- Willing to pay more for best performance --> Zen
```

### Quick Recommendations

| If you are... | Choose... |
| :--- | :--- |
| Learning OpenCode, have your own API key | Free |
| Budget-conscious, want generous limits | Go |
| Want the best coding performance | Zen |
| Enterprise/ team with compliance needs | Enterprise |

---

## Product Comparison Deep Dive

### Model Performance

| Tier | Model Quality | Reliability | Benchmarking |
| :--- | :--- | :--- | :--- |
| **Free** | Varies (depends on your API) | Depends on provider | None |
| **Go** | Good (open-source) | High | Curated selection |
| **Zen** | Excellent (optimized) | Very high | Full benchmarking |
| **Enterprise** | Custom | Custom | Custom |

### Privacy & Security

| Product | Data Stored | Training Use | Compliance |
| :--- | :--- | :--- | :--- |
| **Free** | Depends on provider | Depends on provider | Provider-dependent |
| **Zen** | US-based only | Zero-retention | Provider-compliant |
| **Go** | US-based only | Zero-retention | Provider-compliant |
| **Enterprise** | None (self-hosted) | None | Your controls |

### Use with Other Agents

All OpenCode products (Zen, Go, Enterprise) work with any coding agent, not just OpenCode CLI. This means you can use Zen or Go with:
- Claude Code
- Cursor
- Windsurf
- Other AI coding assistants

---

## Configuration Examples

### Using Zen with OpenCode

```json
{
  "model": "zen",
  "zen": {
    "apiKey": "your-zen-api-key"
  }
}
```

### Using Go with OpenCode

```json
{
  "model": "go",
  "go": {
    "apiKey": "your-go-api-key"
  }
}
```

For detailed configuration instructions, visit [OpenCode Docs](https://opencode.ai/docs).

---

## Summary

OpenCode provides a spectrum of options from free (bring your own key) to premium (Zen) to budget-friendly (Go) to enterprise (self-hosted). Choose based on your budget, performance needs, and privacy requirements.

- **Free**: Your API key, your choice
- **Go**: $10/month, open-source models, generous limits
- **Zen**: Pay-as-you-go, curated for coding, highest performance
- **Enterprise**: Self-hosted, zero data retention, SSO integration

For the latest pricing and product updates, always check [opencode.ai](https://opencode.ai).