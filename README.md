# MiniMax H3 on Kaggle — Wan2GP + Turbo LoRA

Run **MiniMax H3 FL2VA Pruned 20B** on Kaggle using **Wan2GP**.

Large model files are kept in `/tmp` to avoid filling Kaggle’s limited `/kaggle/working` storage.

## What’s Included

- MiniMax H3 FL2VA Pruned INT8 ConvRot (~21 GB)
- Qwen3-VL 32B INT8 text encoder
- Wan2GP + Gradio interface
- Support for MiniMax H3 Turbo LoRA
- GPU / disk checks
- Automatic downloads from Hugging Face

## Requirements

- Kaggle Notebook
- Single T4
- Internet access enabled
- Enough free space in `/tmp`

> **Note:** Wan2GP uses only **one GPU**. Selecting T4 x2 does **not** combine the two cards’ VRAM.

## Quick Start

1. Open `minimax-h3-wan2gp-kaggle.ipynb`
2. Set Accelerator → T4
3. Turn **Internet** On
4. Run all cells from top to bottom
5. Keep the last cell running and open the Gradio URL it prints

## Model Files

| Component              | Path |
|------------------------|------|
| Main Checkpoint        | `/tmp/minimax_h3/MiniMax-H3-FL2VA-pruned_int8_convrot.safetensors` |
| Text Encoder           | `/tmp/minimax_h3/Qwen3-VL-32B-Instruct/Qwen3-VL-32B-Instruct-layer50_quanto_bf16_int8.safetensors` |
| Video / Audio VAE      | Use the ones already registered in Wan2GP for MiniMax H3 |

Source model: [DeepBeepMeep/MiniMax-H3](https://huggingface.co/DeepBeepMeep/MiniMax-H3)

## Turbo LoRA (Recommended)

```text
minimax_h3_turbo_v4_step600_ema.safetensors
```

Source: [larryvrh/MiniMax-H3-Turbo-Lora](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora) (~780 MB)

## Suggested First Test Settings

```text
Model:          MiniMax H3 / FL2VA Pruned 20B
Resolution:     480p
Duration:       ~5 seconds (124 frames)
Steps:          6
LoRA strength:  1.0
Scheduler:      simple (if available)
```

Keep other acceleration methods **off** for the first run.

## Storage Notes

- Large files go to `/tmp/minimax_h3/`
- Generated videos are saved to `/kaggle/working/Wan2GP/outputs/`
- The notebook does **not** contain model weights — they are downloaded at runtime.

## Performance Expectations

MiniMax H3 is large. Even with the Turbo LoRA (fewer steps), generation on a single Kaggle GPU (T4) is relatively slow. Speed depends on resolution, frames, steps, and offloading settings.

## Credits

- [MiniMax H3](https://huggingface.co/DeepBeepMeep/MiniMax-H3)
- [Wan2GP](https://github.com/deepbeepmeep/Wan2GP)
- [MiniMax H3 Turbo LoRA](https://huggingface.co/larryvrh/MiniMax-H3-Turbo-Lora)
