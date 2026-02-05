# Architecture Decision Record: LoRA vs Full Fine-Tuning

## Status
Accepted

## Context
I needed to fine-tune a language model for generating customer service responses. I had to choose between full fine-tuning (updating all model parameters) and LoRA (adding small adapter layers).

## Decision
I chose **LoRA (Low-Rank Adaptation)** for this fine-tuning task.

## Rationale

**Why LoRA:**
- Training time: 10-15 minutes vs 2+ hours for full fine-tuning
- Memory usage: Can fit in 8GB RAM vs needing 16GB+ for full training
- Model size: LoRA adapters are only ~5MB vs 500MB for full model
- Good enough: For this simple response generation task, LoRA quality is sufficient

**Tradeoffs:**
- LoRA might give slightly lower quality than full fine-tuning
- LoRA requires keeping base model + adapters (but total is still smaller)
- LoRA is newer technology, slightly less documentation

**Other Decisions:**
- Chose DistilGPT-2 over GPT-2: faster training, good for learning
- Chose customer service task: simple, easy to evaluate, practical
- Chose 3 evaluation slices: covers different input types without being excessive

## Consequences
- Quick iteration on training
- Easy to share results (small files)
- Can run multiple experiments if needed
- Slightly limited in maximum possible quality
