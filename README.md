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
| –      | –          | –       | 0-shot    | [21.7](https://drive.google.com/file/d/1SEtF8M2fqrZTAU9eCAvna9oipBApTmR1/view?usp=share_link) | [18.0](https://drive.google.com/file/d/1e9GOPhqh0u-we4-5uzBdbS6z37HHgAnT/view?usp=share_link) | [40.8](https://drive.google.com/file/d/1xu5jSnzOHo8w_IGSny5x4gUd0eAQB_0U/view?usp=share_link) | [ckpt]()   |
| ✓      |            |         | Naive SFT | [23.7](https://drive.google.com/file/d/1y-hN004BOhmWVxYqRv-BJfQgegKvB8V2/view?usp=share_link) | [19.4](https://drive.google.com/file/d/18QV4fjgAPwfhmVL9mwOQbdBC3h03C3sg/view?usp=share_link) | [38.1](https://drive.google.com/file/d/1190owb_6yqHSX90CDfQ1gWy9oq97LctC/view?usp=share_link) | [ckpt](https://drive.google.com/file/d/1Siv6tNfyx4us8w0Lp__NcFb7yvaU_U6b/view?usp=share_link)   |
|        |            | ✓       | Naive SFT | [42.8](https://drive.google.com/file/d/1AZjokP93XR6gQz04cp0VVgiHZhJX4X7B/view?usp=share_link) | [39.2](https://drive.google.com/file/d/19bVk9g8uklci2SD6pCf9Ey9V1_RcAYM8/view?usp=share_link) | [46.2](https://drive.google.com/file/d/1cOrlAnijAdmzvf3akHZuRIjPMbF7m0Wb/view?usp=share_link) | [ckpt](https://drive.google.com/file/d/1TUllEAcqQBS6QwfvAWgzYkaAPBNcgr2g/view?usp=share_link)   |
| ✓      |            | ✓       | Naive SFT | [45.9](https://drive.google.com/file/d/1ql3qW75Uid_WGpAir12wrCzBj8zGr96F/view?usp=share_link) | [40.8](https://drive.google.com/file/d/1i_aRSIuqys-DoiN8IQPlaREGoKs5aulT/view?usp=share_link) | [48.6](https://drive.google.com/file/d/1Hlt0xjeU6jXcyHk9p6sLK_S20BcnbfJP/view?usp=share_link) | [ckpt](https://drive.google.com/file/d/1TUllEAcqQBS6QwfvAWgzYkaAPBNcgr2g/view?usp=share_link)   |
| ✓      | ✓          | ✓       | Naive SFT | [46.0](https://drive.google.com/file/d/1XvGt5Egm49MPx19WbZej2LgJlDmBi3W8/view?usp=share_link) | [40.9](https://drive.google.com/file/d/1B8TtYe7GbaXLADSOXDr_EcGUr4t48LyB/view?usp=share_link) | [51.3](https://drive.google.com/file/d/1ULBWWcWOJYoG6VrBMj156jDXcstxM_Vl/view?usp=share_link) | [ckpt](https://drive.google.com/file/d/174IzsjO8X2dl4T6DP5mzBeTYTes0-Hx6/view?usp=share_link)   |
| ✓      | ✓          | ✓       | RoG SFT   | [49.9](https://drive.google.com/file/d/1IgB-FUTpHfg9PrM2l5_FU1ydBCjLPiTP/view?usp=share_link) | [44.7](https://drive.google.com/file/d/1Siv6tNfyx4us8w0Lp__NcFb7yvaU_U6b/view?usp=share_link) | [52.2](https://drive.google.com/file/d/1j3SZufAFqfXXuJUSTMgXHV9IPdlfJTvk/view?usp=share_link) | [ckpt](https://drive.google.com/file/d/1ghmdqu3xEdZWBJ_jj_7AlUcZdab314pb/view?usp=share_link)   |

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
