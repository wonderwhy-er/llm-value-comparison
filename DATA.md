# LLM Value Comparison - Data Reference

## Core Formula
```
Value Score = (Tokens/Day × Quality%) / Cost/Day
```

Higher score = better value per dollar spent.

---

## LOCAL MODELS (RTX 3090 baseline speeds)

| Model | Tokens/sec | Quality % | Notes |
|-------|------------|-----------|-------|
| GPT-OSS-20B | 60-150 | 68% | ChatGPT research, 100 tok/s avg |
| GLM-4.7 Flash | 40-80 | 72% | 60 tok/s typical |
| Llama 3.1 70B Q4 | 20-30 | 82% | Needs 40GB+ VRAM |
| Qwen 2.5 32B | 40-50 | 78% | Good balance |
| Mistral 7B | 70-100 | 65% | Fast but lower quality |

## HARDWARE SPEED MULTIPLIERS (vs RTX 3090)

| Hardware | Approx Cost | Speed Multiplier |
|----------|-------------|------------------|
| RTX 3090 Build | $2,500 | 1.0x |
| RTX 4090 Build | $4,000 | 1.8x |
| RTX 5090 Build | $5,500 | 2.5x |
| Mac M3 Max 64GB | $4,000 | 0.7x |
| Mac M4 Max 128GB | $6,000 | 0.9x |

---

## CLOUD SUBSCRIPTIONS

| Service | Monthly $ | Est. Tokens/Day | Quality % |
|---------|-----------|-----------------|-----------|
| Claude Opus 4.5 | $100 | 45,000 | 95% |
| Claude Sonnet 4.5 | $20 | 75,000 | 88% |
| ChatGPT-4o | $20 | 80,000 | 85% |
| Gemini 1.5 Pro | $20 | 100,000 | 83% |

---

## NOTES TO UPDATE

1. **Token limits are estimates** - actual limits vary by usage patterns
2. **Quality scores** based on MMLU/HumanEval composite
3. **Speed varies** with context length, quantization, runtime
4. Add electricity costs (~$0.50/day for 8hr heavy use)

## TODO
- [ ] Add API pricing comparison (pay-per-token)
- [ ] Add more local models (DeepSeek, etc.)
- [ ] Factor in rate limits more precisely
- [ ] Add latency/streaming considerations
