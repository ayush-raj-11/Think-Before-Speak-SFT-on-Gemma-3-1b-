# 🧠 Teaching Gemma to Reason  
## Supervised Fine-Tuning of Gemma-3-1B using Tunix on TPU

> **Goal:** Train a compact open-weight LLM to *reason before answering* using structured supervision, not just predict tokens.

---

## 📌 Project Overview

Large Language Models often produce correct answers without transparent reasoning.  
This project focuses on **explicit reasoning alignment** by fine-tuning **Gemma-3-1B** using **Supervised Fine-Tuning (SFT)** with **Tunix** on **TPU** infrastructure.

Instead of optimizing for final answers alone, the model is trained on a strict format:


This encourages:
- Stable reasoning behavior  
- Better interpretability  
- More predictable outputs  

---

## 🚀 Why This Project Matters

Most open-source fine-tuning tutorials:
- Skip reasoning supervision  
- Jump directly to RL  
- Ignore training stability  

**My opinion:**  
> Reinforcement Learning cannot fix weak reasoning foundations.  
> Strong reasoning must be *taught*, not *rewarded later*.

This project builds that foundation correctly.

---

## 🧠 Model Details

| Component | Description |
|---------|------------|
| Base Model | Gemma-3-1B (open-weight) |
| Training Method | Supervised Fine-Tuning (SFT) |
| Framework | Tunix |
| Hardware | TPU |
| Task Focus | Mathematical & logical reasoning |
| Output Style | Explain-then-answer |

---

## 📂 Dataset

- Primary dataset: **GSM8K**
- Each sample is reformatted into:
  - `question`
  - `reasoning`
  - `final_answer`

### Example Training Format

```text
Question:
If a train travels 60 km in 1 hour, how long will it take to travel 180 km?

Reasoning:
The speed is 60 km per hour. To travel 180 km, divide 180 by 60.
180 ÷ 60 = 3.

Answer:
3 hours
