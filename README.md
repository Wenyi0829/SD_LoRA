# Style Adaptation for Stable Diffusion XL using LoRA

This project demonstrates the effectiveness of **Low-Rank Adaptation (LoRA)** for customizing **Stable Diffusion XL (SDXL)** to generate specific style images. By leveraging parameter-efficient fine-tuning, we achieve significant improvements in style-specific generation using only a minimal dataset.

## 🚀 Key Highlights

- **Data Efficiency:** Successfully fine-tuned using only **10 training images**.
- **Performance Improvement:** Achieved a **7.4% relative improvement** in CLIP score compared to the baseline SDXL.
- **Computational Efficiency:** Training completed in **4 hours** on a single NVIDIA RTX 4090 GPU.
- **Style Consistency:** Enhanced adherence to steam-punk aesthetics (brass, copper, mechanical details, Victorian elements).

## 📊 Results

| Metric | Baseline SDXL | LoRA Fine-tuned SDXL | Improvement |
| :--- | :---: | :---: | :---: |
| **Avg. CLIP Score** | 0.3293 | **0.3537** | +0.0244 |
| **Std. Deviation** | 0.0419 | **0.0178** | -0.0241 |

## 🛠 Methodology

- **Base Model:** Stable Diffusion XL (SDXL) base checkpoint (sd-xl-base-1.0).
- **Fine-tuning Method:** Low-Rank Adaptation (LoRA) applied to attention mechanisms in U-Net and text encoder.
- **Training Script:** Kohya_ss training script.
- **Hyperparameters:**
  - Rank (r): 16
  - Learning Rate: 1e-4 (cosine annealing)
  - Training Steps: 1000
  - Optimizer: AdamW
- **Dataset:** 10 high-quality steam-punk images curated from Pinterest, annotated using BLIP + manual refinement.

## 💻 Inference Usage

The fine-tuned model is designed to be used with **ComfyUI**.

**Recommended Configuration:**
- **Resolution:** 512×512 pixels
- **Sampling:** Euler method (20 steps)
- **Cfg Scale:** 8.0
- **LoRA Strength:**
  - Model Weights: `0.5`
  - CLIP Embeddings: `1.02`

**Example Prompt:**
> "A detailed steampunk mechanical device with brass gears and copper pipes"

📁 model in loras folder

