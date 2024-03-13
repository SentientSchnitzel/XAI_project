# Explainable AI project 
[Project Description](https://docs.google.com/document/d/12DS-Xf361NL-_5QrEJGnx2suSJ1ZaB-hVje6rwk0oL8/edit)




# Concept Bottleneck Models 

![teaser](https://github.com/yewsiang/ConceptBottleneck/blob/master/figures/teaser_landscape.png)

This repository contains code and scripts for the following paper:

> Concept Bottleneck Models
>
> Pang Wei Koh\*, Thao Nguyen\*, Yew Siang Tang\*, Stephen Mussmann, Emma Pierson, Been Kim, and Percy Liang
>
> ICML 2020

The experiments use the following datasets:
- [Caltech-UCSD Birds 200 (CUB)](https://www.vision.caltech.edu/datasets/cub_200_2011/)

To download the TravelingBirds dataset, which we use to test robustness to background shifts, please download the `CUB_fixed` folder from this [CodaLab bundle](https://worksheets.codalab.org/bundles/0x518829de2aa440c79cd9d75ef6669f27) by clicking on the download button. If you use this dataset, please also cite the original CUB and Places datasets.

Here, we focus on scripts replicating our results on CUB, which is public. We provide an executable, Dockerized version of those experiments on [CodaLab](https://worksheets.codalab.org/worksheets/0x362911581fcd4e048ddfd84f47203fd2).

## Abstract

We seek to learn models that we can interact with using high-level concepts:
would the model predict severe arthritis if it thinks there is a bone spur in the x-ray?
State-of-the-art models today do not typically support the manipulation of concepts like "the existence of bone spurs",
as they are trained end-to-end to go directly from raw input (e.g., pixels) to output (e.g., arthritis severity).
We revisit the classic idea of first predicting concepts that are provided at training time,
and then using these concepts to predict the label.
By construction, we can intervene on these _concept bottleneck models_
by editing their predicted concept values and propagating these changes to the final prediction.
On x-ray grading and bird identification, concept bottleneck models achieve competitive accuracy with standard end-to-end models,
while enabling interpretation in terms of high-level clinical concepts ("bone spurs") or bird attributes ("wing color").
These models also allow for richer human-model interaction: accuracy improves significantly if we can correct model mistakes on concepts at test time.

![teaser](https://github.com/yewsiang/ConceptBottleneck/blob/master/figures/tti_qual_examples.png)

## Prerequisites
We used the same environment as Codalab's default gpu setting, please run `pip install -r requirements.txt`. Main packages are:
- matplotlib 3.1.1
- numpy 1.17.1
- pandas 0.25.1
- Pillow 6.2.2
- scipy 1.3.1
- scikit-learn 0.21.3
- torch 1.1.0
- torchvision 0.4.0

Note that we updated Pillow and removed tensorflow-gpu and tensorboard from requirements.txt.  

### Docker
You can pull the Docker image directly from Docker Hub.
```
docker pull codalab/default-gpu
```

## Usage
Standard task training for CUB can be ran using the `scripts/experiments.sh` and Codalab scripts can be ran using `scripts/codalab_experiments.sh`. More information about how to perform data processing and other evaluations can be found in the README in `CUB/`.
