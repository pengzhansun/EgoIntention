# Visual Intention Grounding for Egocentric Assistants (ICCV 2025)

[![Paper](https://img.shields.io/badge/Paper-arXiv:2504.13621-B31B1B)](https://arxiv.org/abs/2504.13621)  
[![Conference](https://img.shields.io/badge/ICCV-2025-blue)](https://iccv2025.thecvf.com/)  
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

- [Introduction](#introduction)
- [Challenge](#challenge)
- [Dataset](#dataset)
- [Method](#method)
- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Checkpoints](#checkpoints)
- [Acknowledgments](#acknowledgments)
- [Citation](#citation)
- [Contact](#contact)

---

## Introduction

Egocentric AI assistants must understand **human intentions** that are often implicit, context-dependent, and not explicitly tied to object names.  
We introduce **EgoIntention**, the first dataset for *egocentric visual intention grounding*, where models must localize objects in first-person views based on natural intention queries.

<div align="center">
  <img width="500" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_teaser.jpg"/>
</div>


---

## Challenge

Models must resist distractions from unintended objects and reason about **uncommon functionalities** of objects.  

Example: In the query *“gather my phone and belongings”*, existing models often wrongly ground **phone** (explicitly mentioned), while the correct target is **handbag** (implicitly intended).

<div align="center">
  <img width="500" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_challenge.jpg"/>
</div>

---

## Dataset

We build on PACO’s egocentric image splits and annotate **intention queries with bounding boxes**.

- **15,667** training samples  
- **825** validation samples  
- **9,892** test samples  
- Two query types:  
  - **Context intentions** – leveraging environmental cues  
  - **Uncommon intentions** – alternative object functionalities  

<div align="center">
  <img width="500" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_collection.jpg"/>
</div>

🔗 Download:  
- [PACO-Ego4D source images](https://ego4d-data.org/)  
- [EgoIntention annotations (Google Drive)](https://drive.google.com/drive/folders/1pLuM1oZK8ULUPZenPShrEpHaggKXVj5H?usp=sharing)  

---

## Method

We introduce **Reason-to-Ground (RoG)** instruction tuning:  
- Performs *counterfactual analysis* by comparing factual vs. counterfactual inference outcomes.  
- Bridges **normal descriptions** and **egocentric intentions**.  
- Outperforms naive fine-tuning and hybrid training strategies.

<div align="center">
  <img width="650" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_method.jpg"/>
</div>

---

## Requirements

```bash
git clone https://github.com/pengzhansun/EgoIntention.git
cd EgoIntention
pip install -r requirements.txt
