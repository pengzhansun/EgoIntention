# Visual Intention Grounding for Egocentric Assistants (ICCV 2025)

[![Paper](https://img.shields.io/badge/Paper-arXiv:2504.13621-B31B1B)](https://arxiv.org/abs/2504.13621)  
[![Conference](https://img.shields.io/badge/ICCV-2025-blue)](https://iccv2025.thecvf.com/)  
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

---

🔗 Download:  
- [PACO-Ego4D source images](https://ego4d-data.org/)  
- [EgoIntention annotations (Google Drive)](https://drive.google.com/drive/folders/1pLuM1oZK8ULUPZenPShrEpHaggKXVj5H?usp=sharing)

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
  <img width="600" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_teaser.jpg"/>
</div>


---

## Challenge

The model must infer the intended object from the full intention sentence, rather than simply detecting explicitly mentioned objects. In this example, “gather my phone and belongings” explicitly mentions “phone” (highlighted in red) , which often misleads existing visual grounding models to identify the wrong object (red box). The correct target, a handbag (green box), is only implied.

<div align="center">
  <img width="300" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_challenge.jpg"/>
</div>

---

## Dataset

We source PACOEgo4D images and annotate **intention queries with bounding boxes**.

- **15,667** training samples  
- **825** validation samples  
- **9,892** test samples  
- Two query types:  
  - **Context intentions** – leveraging environmental cues  
  - **Uncommon intentions** – alternative object functionalities  

<div align="center">
  <img width="600" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_collection.jpg"/>
</div>

🔗 Download:  
- [PACO-Ego4D source images](https://ego4d-data.org/)  
- [EgoIntention annotations (Google Drive)](https://drive.google.com/drive/folders/1pLuM1oZK8ULUPZenPShrEpHaggKXVj5H?usp=sharing)

---

## Method

Our proposed **Reason-to-Ground (RoG)** instruction tuning improves grounding performance by chaining two stages:
1. **Intention reasoning** → infer the explicit object category from the intention.  
2. **Object grounding** → localize the object in the scene.  

RoG enables unified visual grounding across both **egocentric (implicit intentions)** and **exocentric (explicit queries)** perspectives.

<div align="center">
  <img width="300" src="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_method.jpg"/>
</div>

---

## Requirements

🚧 *To be updated — will include dependency installation and environment setup instructions.*

---

## Getting Started

🚧 *To be updated — training, evaluation, and example usage scripts will be added here.*

---

## Checkpoints

🚧 *To be updated — links to pretrained and fine-tuned models will be provided here.*

---

## Acknowledgments



---

## Citation

If you find this project useful, please cite:

```bibtex
@article{sun2025visual,
  title={Visual Intention Grounding for Egocentric Assistants},
  author={Sun, Pengzhan and Xiao, Junbin and Tse, Tze Ho Elden and Li, Yicong and Akula, Arjun and Yao, Angela},
  journal={arXiv preprint arXiv:2504.13621},
  year={2025}
}
```
