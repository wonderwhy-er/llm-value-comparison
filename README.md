# LLM Value Comparison: Local vs Cloud

**Live Tool:** [https://wonderwhy-er.github.io/llm-value-comparison/](https://wonderwhy-er.github.io/llm-value-comparison/)

An interactive calculator to compare the **value** of running local LLMs vs cloud subscriptions.

## The Core Metric

**Quality-Adjusted Tokens per Dollar**

```
Value = Total Quality-Adjusted Tokens / Total Cost
```

This normalizes the comparison to: *"How many useful tokens do I get per dollar spent?"*

## What It Calculates

### Local Setup
```
tokens/sec × 3600 sec/hr × hours/day = tokens/day
tokens/day × quality% = quality-adjusted tokens/day
quality-adjusted/day × 365 × years = total tokens
total tokens / hardware cost = tokens per dollar
```

### Cloud Subscription
```
token limit/day × efficiency% = effective tokens/day
effective/day × quality% = quality-adjusted tokens/day  
quality-adjusted/day × 365 × years = total tokens
$/month × 12 × years = total cost
total tokens / total cost = tokens per dollar
```

## Data Sources

### Local Models (RTX 3090 baseline)
| Model | Tokens/sec | Quality % |
|-------|------------|-----------|
| GPT-OSS-20B | 100 | 68% |
| GLM-4.7 Flash | 60 | 72% |
| Llama 3.1 70B Q4 | 25 | 82% |
| Qwen 2.5 32B | 45 | 78% |
| Mistral 7B | 80 | 65% |

### Cloud Subscriptions (estimated daily limits)
| Service | Price | Tokens/Day | Quality % |
|---------|-------|------------|-----------|
| Claude Pro | $20/mo | ~220K | 88% |
| Claude Max 5× | $100/mo | ~440K | 95% |
| Claude Max 20× | $200/mo | ~1.1M | 95% |
| ChatGPT Plus | $20/mo | ~80K | 85% |
| ChatGPT Pro | $200/mo | ~500K | 90% |

**Note:** Claude limits are based on 5-hour rolling windows (~44K/88K/220K per window × ~5 resets/day).

## Contributing

This is an ongoing evaluation. Contributions welcome:
- More accurate benchmark quality scores
- Updated token limits from real usage
- Additional models and services
- Hardware speed multipliers for different GPUs

## License

MIT
