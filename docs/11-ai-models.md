# AI Models Guide

Choosing the right AI model is crucial for your OpenCode experience. This guide covers model options, from free to premium, including how to maximize value.

---

## Quick Comparison

| Option | Cost | Quality | Setup Complexity | Best For |
| :--- | :--- | :--- | :--- | :--- |
| **Bring Your Own Key** | You pay API costs | Varies | Medium | Already have API credits |
| **Antigravity (Plugin)** | Free | High | Easy | Free premium models |
| **OpenCode Go** | $5-10/mo | Good | Easy | Budget users |
| **OpenCode Zen** | Pay-as-you-go | Excellent | Easy | Performance-focused |
| **Self-hosted** | Hardware costs | Varies | Hard | Privacy/specialized needs |

---

## Option 1: Bring Your Own API Key

Use any LLM provider by adding your own API key.

### Supported Providers

| Provider | Models | Setup |
| :--- | :--- | :--- |
| **OpenAI** | GPT-4, GPT-4o, o1 | Get key from openai.com |
| **Anthropic** | Claude 3.5, Claude 3 | Get key from anthropic.com |
| **Google** | Gemini 1.5, Gemini 2.0 | Get key from aistudio.google.com |
| **Mistral** | Mistral Large, Codestral | Get key from mistral.ai |
| **Local Models** | Various | Ollama, LM Studio, etc. |

### Configuration

```json
{
  "model": "claude-3-5-sonnet-20241022",
  "anthropicApiKey": "sk-ant-api03-xxxxxxxx"
}
```

Or use environment variables:

```bash
export ANTHROPIC_API_KEY="sk-ant-api03-xxxxxxxx"
export OPENAI_API_KEY="sk-xxxxxxxx"
```

### Finding Model Names

Check provider documentation for current model names:

- OpenAI: `gpt-4o`, `gpt-4o-mini`, `o1-preview`
- Anthropic: `claude-3-5-sonnet-20241022`, `claude-3-opus-20240229`
- Google: `gemini-1.5-pro`, `gemini-2.0-flash`

---

## Option 2: Antigravity (Free Premium Models)

Access high-end models like Claude Opus and Gemini 3.1 Pro completely free through Google's Antigravity IDE OAuth.

### Requirements

1. Install the plugin:
   ```bash
   opencode plugin add opencode-antigravity-auth
   ```

2. Authenticate with Google through Antigravity IDE

### Available Models (Free)

| Model | Quality | Use Case |
| :--- | :--- | :--- |
| **Claude Opus** | Highest | Complex reasoning, best coding |
| **Gemini 3.1 Pro** | Very High | Balanced, fast |
| **Gemini 2.0** | High | Latest features |

### Why This Matters

- Claude Opus typically costs $15/1M tokens
- Gemini 3.1 Pro typically costs $3/1M tokens
- Antigravity provides free access to both

### Best For

- Budget-conscious developers
- Trying premium models without cost
- Accessing Claude Opus for complex tasks

---

## Option 3: OpenCode Go ($5-10/month)

Low-cost subscription with generous limits and reliable access to open-source models.

### Pricing

- First month: $5
- Ongoing: $10/month
- Optional top-up credits available

### Included Models

| Model | Requests/5hr | Strength |
| :--- | :--- | :--- |
| DeepSeek V4 Flash | 31,650 | Fast, capable |
| DeepSeek V4 Pro | 10,200 | Better reasoning |
| Qwen3.5 Plus | 3,600 | General coding |
| Qwen3.6 Plus | 400 | Latest Qwen |
| Kimi K2.5/2.6 | up to 440 | Chinese models |
| MiniMax M2.5/2.7 | up to 750 | Balanced |
| GLM-5/5.1 | up to 1,080 | Chinese flagship |

### Configuration

```json
{
  "model": "go",
  "go": {
    "apiKey": "your-go-api-key"
  }
}
```

### Best For

- Predictable monthly cost
- Generous usage limits
- Open-source model preference

---

## Option 4: OpenCode Zen (Pay-as-you-go)

Curated, benchmark-tested models optimized for coding agents.

### Pricing

- Add $20 minimum balance
- Pay per request with zero markup
- Auto-top up at $5 threshold

### How Models Are Selected

OpenCode tests and benchmarks models specifically for:
- Code generation quality
- Instruction following
- Tool use accuracy
- Reasoning capabilities

### Configuration

```json
{
  "model": "zen",
  "zen": {
    "apiKey": "your-zen-api-key"
  }
}
```

### Best For

- Best coding performance
- No testing needed
- Willing to pay for quality

---

## Option 5: Self-Hosted / Local Models

Run models on your own hardware for privacy or specialized needs.

### Options

| Tool | Description | Setup |
| :--- | :--- | :--- |
| **Ollama** | Local model runner | ollama.com |
| **LM Studio** | Desktop model manager | lmstudio.ai |
| **Text Generation Webui** | Web interface | github.com/oobabooga |
| **KoboldCPP** | Efficient local | github.com/lostru名 |

### Configuration for Local

```json
{
  "model": "llama3:70b",
  "baseUrl": "http://localhost:11434"
}
```

### Best For

- Privacy-sensitive work
- No internet dependency
- Fine-tuned custom models
- Hardware you already have

---

## Model Selection Guide

### By Task Type

| Task | Recommended Model |
| :--- | :--- |
| **Simple edits/fixes** | GPT-4o Mini, Gemini Flash, Qwen |
| **Feature development** | Claude 3.5 Sonnet, GPT-4o, DeepSeek V4 |
| **Complex refactoring** | Claude 3 Opus, Gemini Pro |
| **Architecture decisions** | Claude 3 Opus, GPT-4 |
| **Debugging** | Claude 3.5 Sonnet, DeepSeek V4 |
| **Learning/exploring** | Any capable model |

### By Budget

| Budget | Recommendation |
| :--- | :--- |
| **$0** | Antigravity (free premium) or bring your own free tier |
| **$5-10/mo** | OpenCode Go |
| **$20-50/mo** | OpenCode Zen or pay-as-you-go API |
| **$50+/mo** | OpenCode Zen + premium API |

---

## Performance Tips

### 1. Context Settings

```json
{
  "context": "high"  // More context = better results for complex tasks
}
```

### 2. Temperature

```json
{
  "temperature": 0.7  // 0.0-1.0, lower = more focused, higher = more creative
}
```

### 3. System Prompts

Add custom instructions in config:

```json
{
  "systemPrompt": "You are an expert React developer. Always prefer functional components with hooks."
}
```

---

## Troubleshooting

| Issue | Solution |
| :--- | :--- |
| API errors | Check API key is valid and has credits |
| Rate limits | Use model with higher limits or upgrade |
| Slow responses | Try faster models (Flash/Mini variants) |
| Quality issues | Upgrade to more capable model |
| Wrong model loaded | Verify model name in config |

---

## Related Sections

- [OpenCode Products](08-opencode-products.md) - Zen, Go, Enterprise details
- [Plugins Guide](09-plugins-guide.md) - Antigravity plugin
- [Command Reference](00-command-reference.md) - Model config options