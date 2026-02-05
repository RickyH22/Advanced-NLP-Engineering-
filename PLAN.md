# Fine-Tuning Plan

## Model Choice
I chose **DistilGPT-2** as the base model because:
- It's small and trains quickly on regular hardware
- Good for learning fine-tuning without expensive compute
- Still produces decent results for text tasks

## Training Approach: LoRA
I decided to use **LoRA (Low-Rank Adaptation)** instead of full fine-tuning because:
- Much faster training time (important for this assignment)
- Uses less memory - can run on my laptop
- Smaller model files to save and share
- Good enough performance for this task

## Task
Fine-tune the model to generate positive customer review responses based on review text.

## Evaluation Slices
I will evaluate the model on three specific slices:

1. **Short Reviews** (< 50 characters): Test if model handles brief feedback
2. **Long Reviews** (> 150 characters): Test if model maintains coherence with detailed input
3. **Negative Keywords** (contains "bad", "terrible", "disappointing"): Test if model responds appropriately to criticism

## Success Metric
- **Primary**: Perplexity < 15 on validation set (lower is better)
- **Secondary**: Manual review of 20 samples - at least 70% should be appropriate responses
- **Slice-specific**: No slice should have >2x worse perplexity than overall average
