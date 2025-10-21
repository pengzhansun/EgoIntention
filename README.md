# Visual Intention Grounding for Egocentric Assistants (ICCV 2025)

[![Paper](https://img.shields.io/badge/Paper-arXiv:2504.13621-B31B1B)](https://openaccess.thecvf.com/content/ICCV2025/papers/Sun_Visual_Intention_Grounding_for_Egocentric_Assistants_ICCV_2025_paper.pdf)  [![Conference](https://img.shields.io/badge/ICCV-2025-blue)](https://iccv.thecvf.com)  [![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

🔗 Download:  
- [PACO-Ego4D source images](https://ego4d-data.org/)  [PACO github repo](https://github.com/facebookresearch/paco)
- [EgoIntention annotations (Google Drive)](https://drive.google.com/drive/folders/1pLuM1oZK8ULUPZenPShrEpHaggKXVj5H?usp=sharing)

---

- [Introduction](#introduction)
- [Challenge](#challenge)
- [Dataset](#dataset)
- [Method](#method)
- [Checkpoints](#checkpoints)
- [Acknowledgments](#acknowledgments)
- [Citation](#citation)

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
- [PACO-Ego4D source images](https://ego4d-data.org/)  [PACO github repo](https://github.com/facebookresearch/paco)
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

## Checkpoints

Each row corresponds to an SFT configuration used for MiniGPT-v2 fine-tuning.  

| RC/+/g | RCInt./+/g | EgoInt. | Method    | Context | Uncommon | Object | Checkpoint |
|:------:|:----------:|:-------:|:---------:|:------:|:--------:|:------:|:----------:|
| –      | –          | –       | 0-shot    | [21.7]() | [18.0]() | [40.8]() | [ckpt]()   |
| ✓      |            |         | Naive SFT | [23.7]() | [19.4]() | [38.1]() | [ckpt]()   |
|        |            | ✓       | Naive SFT | [42.8]() | [39.2]() | [46.2]() | [ckpt]()   |
| ✓      |            | ✓       | Naive SFT | [45.9]() | [40.8]() | [48.6]() | [ckpt]()   |
| ✓      | ✓          | ✓       | Naive SFT | [46.0]() | [40.9]() | [51.3]() | [ckpt]()   |
| ✓      | ✓          | ✓       | RoG SFT   | [49.9]() | [44.7]() | [52.2]() | [ckpt]()   |

---

## Acknowledgments

We would like to thank the following open-source contributions that made this work possible:

- [MiniGPT-v2](https://github.com/Vision-CAIR/MiniGPT-4) for their awesome open-source vision-language model.
- [PACO](https://github.com/facebookresearch/paco) for their valuable dataset contribution.

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
