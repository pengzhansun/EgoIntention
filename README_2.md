
## Visual Intention Grounding for Egocentric Assistants (ICCV 2025)

- [Introduction](#introduction)
- [Challenge](#challenge)
- [Dataset](#dataset)
- [Method](#method)
- [Requirements](#requirements)
- [Getting Started](#getting-started)
- [Checkpoints](#checkpoints)
- [Acknowledgments](#acknowledgments)
- [Citation](#citation)


## Introduction

<div align=center><img width = '400' src ="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_teaser.pdf"/></div>
On the other hand, the object appearance is a meaningful cue which can help the model to learn the knowledge of action.

## Challenge

<div align=center><img width = '400' src ="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_challenge.pdf"/></div>
are 174 action categories with 54,919 training and 57,876 validation instances. More details can be found in Something-Else.

## Dataset

<div align=center><img width = '400' src ="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_collection.pdf"/></div>
Download sourced images from [pacoEgo4D]() and our [EgoIntention annotation](https://drive.google.com/drive/folders/1pLuM1oZK8ULUPZenPShrEpHaggKXVj5H?usp=sharing).

## Method
We empower models the ability of counterfactual analysis so that a more accurate classification result can be gained by comparing factual inference outcome and counterfactual inference outcome.

<div align=center><img width = '600' src ="https://github.com/pengzhansun/EgoIntention/blob/main/Figures/cr_method.pdf"/></div>



## Requirements
```
pip install -r requirements.txt
```

## Getting Started
To train, test or , please run these [scripts]().

## Checkpoints
Download [our models]() reported on the paper. 

## Citation
If you use this code repository in your research, please cite this project.

```
@article{sun2025visual,
  title={Visual Intention Grounding for Egocentric Assistants},
  author={Sun, Pengzhan and Xiao, Junbin and Tse, Tze Ho Elden and Li, Yicong and Akula, Arjun and Yao, Angela},
  journal={arXiv preprint arXiv:2504.13621},
  year={2025}
}
```


## Acknowledgments
This repository is implemented as a fork of [MiniGPTv2](https://github.com/joaanna/something_else). We used parts of code from following repositories:


Contact: pengzhansun6@gmail.com
