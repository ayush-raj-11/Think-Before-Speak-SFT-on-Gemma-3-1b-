# 🧠 Gemma, Trained to Think  
### Reasoning-First Supervised Fine-Tuning on TPU using Tunix

> **Not bigger models. Better thinking.**

This repository documents a **reasoning-centric fine-tuning experiment** where **Gemma-3-1B** is trained to *internalize step-by-step logic* through **structured supervision**, executed efficiently on **TPU** using **Tunix**.

---

## 🔬 Core Idea

Most LLM fine-tuning pipelines optimize for:
- Output fluency  
- Answer accuracy  
- Instruction following  

This project optimizes for something more fundamental:

> **Cognitive structure.**

The model is trained to:
1. Pause  
2. Reason  
3. Answer  

This is enforced **during training**, not patched later with reinforcement learning.

---

## 🧠 Why Reasoning-First Matters

In many RL-aligned systems:
- Reasoning is emergent  
- Errors are masked by reward shaping  
- Failures are hard to diagnose  

**Opinionated take:**  
> RL refines behavior.  
> SFT defines thinking.

This repository focuses entirely on **defining how the model thinks**.

---

## 🧩 Model & Stack

| Layer | Choice | Reason |
|------|------|-------|
| Base Model | Gemma-3-1B | Small, fast, transparent |
| Training Paradigm | Supervised Fine-Tuning | Stable reasoning acquisition |
| Framework | Tunix | TPU-native, scalable |
| Compute | TPU (JAX) | High-throughput, low-latency |
| Objective | Reasoning Alignment | Not just accuracy |

---

## 📘 Dataset Philosophy

Instead of raw Q&A, each sample encodes **explicit cognition**.

### Training Schema

```text
<QUESTION>
<DELIBERATE REASONING>
<FINAL ANSWER>


Question:
A shopkeeper sells an item for ₹240 after a 20% discount. What was the original price?

Reasoning:
A 20% discount means the selling price is 80% of the original.
Let the original price be x.
0.8x = 240
x = 240 / 0.8 = 300

Answer:
₹300


Raw Reasoning Data
        ↓
Normalization & Structural Enforcement
        ↓
Tokenizer Alignment
        ↓
TPU Mesh Configuration
        ↓
SFT with Tunix
        ↓
Reasoning-Aware Evaluation
