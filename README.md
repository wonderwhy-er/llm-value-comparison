# LLM Value Comparison

**Compare the value of Local Hardware vs Subscriptions vs API pricing**

🔗 **Live Demo:** https://wonderwhy-er.github.io/llm-value-comparison/

## What is this?

A tool to calculate and compare the **quality-adjusted tokens per dollar** across three ways to access LLMs:

1. **🖥️ Local** - One-time hardware cost, unlimited usage
2. **💳 Subscription** - Monthly fee, daily token limits (⚠️ estimated)
3. **🔌 API** - Pay per token

## Features

- **📊 Calculator** - Ranked comparison of all models/services
- **📈 Timeline Chart** - Value trends over time by provider
- **📋 Raw Data** - All data in tables with source links

## Local Development

To run locally, you need a web server (browsers block `fetch()` for `file://` URLs):

```bash
# Using npx (recommended)
npx serve

# Or using Python
python3 -m http.server 8888
```

Then open http://localhost:3000 (serve) or http://localhost:8888 (Python).

## The Formula

All three calculate the same metric: **Quality-Adjusted Tokens per Dollar**

### Local
```
(tokens/sec × hours/day × 3600 × 365 × years × quality%) / hardware_cost
```

### Subscription
```
(tokens/day × 365 × years × quality%) / (monthly_price × 12 × years)
```

### API
```
(1,000,000 / price_per_million) × quality%
```

## Data Structure

All data is stored in JSON files under `/data/`:

```
/data/
  index.json           # List of all model IDs
  hardware.json        # Hardware specs, prices, sources
  benchmarks.json      # Benchmark metadata
  /models/
    claude-sonnet-4.json
    gpt-4o.json
    llama-3.1-70b.json
    ...
```

Each model file contains:
- Basic info (name, provider, release date, model card link)
- Benchmark scores with source links
- API pricing with source
- Local performance per hardware with sources
- Subscription options with sources and confidence levels

## Contributing

**This is an open-source project! Please contribute model data via Pull Requests.**

### How to add a new model:

1. Fork the repo
2. Create a new file: `data/models/your-model-id.json`
3. Add the model ID to `data/index.json`
4. Submit a PR

### Model file format:

```json
{
  "id": "model-id",
  "name": "Model Name",
  "provider": "Provider",
  "releaseDate": "YYYY-MM-DD",
  "modelCard": "https://link-to-model-card",
  
  "benchmarks": {
    "arena_elo": { "score": 1300, "source": "https://lmarena.ai/leaderboard" },
    "aider_polyglot": { "score": 45.5, "source": "https://aider.chat/docs/leaderboards/" }
  },
  
  "api": {
    "inputPer1M": 3.00,
    "outputPer1M": 15.00,
    "source": "https://provider.com/pricing"
  },
  
  "local": {
    "rtx_3090": {
      "tokensPerSec": 45,
      "quantization": "Q4_K_M",
      "vramRequired": 24,
      "source": "https://github.com/ggerganov/llama.cpp/discussions/..."
    }
  },
  
  "subscriptions": {
    "service_name": {
      "name": "Service Name",
      "monthlyPrice": 20,
      "tokensPerDay": 200000,
      "confidence": "low",
      "notes": "Explanation of estimate",
      "source": "https://..."
    }
  }
}
```

### Subscription Confidence Levels

- **high** - Official published limits
- **medium** - Derived from official info (e.g., "5x more than free tier")
- **low** - Community estimates, reverse-engineered

### Recommended Benchmarks

| Benchmark | Use Case | Why |
|-----------|----------|-----|
| `arena_elo` | General quality | Human preference, most reliable |
| `aider_polyglot` | Coding | Real-world tasks, tracks cost |
| `livebench` | Knowledge | Contamination-resistant |

Avoid relying solely on MMLU, HumanEval (saturated benchmarks).

## Data Sources

- **Human Preference**: [LMSys Chatbot Arena](https://lmarena.ai/leaderboard)
- **Coding**: [Aider Leaderboard](https://aider.chat/docs/leaderboards/)
- **API Pricing**: [Artificial Analysis](https://artificialanalysis.ai/models)
- **Local Speeds**: [llama.cpp discussions](https://github.com/ggerganov/llama.cpp/discussions)
- **Subscription Limits**: Community research (see individual source links)

## License

MIT License - see [LICENSE](LICENSE)
