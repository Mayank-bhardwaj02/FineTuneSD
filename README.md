# DreamBooth Fine-Tuning for Stable Diffusion 🌟

This repository demonstrates how to fine-tune Stable Diffusion using **DreamBooth** 👟 on a custom shoe dataset. It includes code, hyperparameter configurations, and notes on overcoming GPU/memory challenges 💪.

---

## Project Overview 📋

- **Goal** 🎯: Teach Stable Diffusion to generate new images of a specific shoe, placed in various backgrounds and scenarios.  
- **Method** 🛠️: DreamBooth fine-tuning on ~9 images of the same shoe from different angles 📸.

---

## Changes Made

During the fine-tuning process, I adjusted key hyperparameters:

```bash
--train_batch_size=4
--learning_rate=3e-6
--max_train_steps=1400
```
## Benefits of These Changes

- **Larger Batch Size** 📈: Enables more stable training on a high-VRAM GPU.
- **Lower Learning Rate** ⚖️: Facilitates gradual and precise updates, capturing intricate shoe details.
- **Extended Training Steps** ⏳: Promotes thorough learning while minimizing excessive overfitting.

## Challenges Encountered

### CUDA Version & Driver Issues 🛠️
- Required ensuring the environment aligned with the GPU’s driver and PyTorch specifications.

### Memory Limitations 💾
- Despite using a large GPU, mid-training checkpoints and high-resolution images demanded careful disk space management.
- Occasionally required disabling intermediate checkpoints to mitigate memory constraints.

### Environment Mismatch 🔧
- Needed to update the `diffusers` library to the correct version (`>= 0.33.0.dev0`) to prevent import errors.

## Hardware Specs 💻

- **GPU** 🎮: 48 GB VRAM (peak usage ~30 GB)
- **System RAM** 🧠: 64 GB
- **Disk** 💿: Sufficient space required for storing checkpoints; resolved “No space left on device” errors by clearing out old model folders.

## Future Improvements 🚀

- **Additional Images** 📸: Collect more shoe angles to minimize stylization inconsistencies.
- **Further Hyperparameter Tuning** 🎛️: Test different schedulers, warmup steps, or integrate LoRA for enhanced performance.
- **Mixed Precision** ⚡: Implement FP16 or BF16 to lower VRAM usage, potentially allowing for an increased batch size.
