---
title: "Issues in detecting COVID-19 from X-Rays"
icon: "https://user-images.githubusercontent.com/35240934/175382135-295616a9-b96b-4186-9977-c273ce94e309.png"
date: 2022-05-01
draft: false
project_tags: ["AI", "Python", "JAX", "Pytorch", "DL", "COVID-19", "Google TRC"]
summary: "Mitigating issues of current approaches to image-based COVID-19 diagnosis"
weight: 1
categories: ["research"]
index: 1
---

## About

All source code and instructions to generate the results and figures in the paper are contained [in this repository](https://github.com/JoaoMarcosCSilva/issues-covid-image-diagnosis). The full paper is available [here](https://proceedings.mlr.press/v184/silva22a.html).

Machine Learning (ML) has become a foremost approach for solving real-world problems from data. Supervised learning, in particular, has risen to be a popular method for building models that learn to classify inputs from a set of examples. When developing these models, the overarching goal is to learn a function that can generalize to examples outside of those provided during training. Indeed, fitting a model to a set of training samples is often trivial, in particular with high capacity models such as deep neural networks. However, generalizing to instances outside of training is a much more challenging problem.

In settings where robustness to generalization is critical, such as medical and healthcare studies, black-box models that fail to generalize are particularly problematic and forbid practical utility. ML researchers have explored several approaches for making the models more reliable. [Yang et al., 2021] provides a literature review that describes how explainable AI can aid in developing ML models that work in the real world. For the task of COVID-19 image-based detection specifically, [Ter-Sarkisov, 2020] takes a two step approach that first detects instances of ground glass opacity and consolidation in CT scans, then predicts the patient’s condition using only the ranked bounding box detections (thus making the model able to generalize even with a very small amount of training data). [Teixeira et al., 2021] uses a U-Net CNN architecture to perform semantic segmentation that isolates the lungs on CXR scans before trying to classify whether the patient has COVID-19, but still finds that a strong bias from underlying data source issues severely hampers results. Our work investigates current issues with some of the most popular datasets used for COVID-19 diagnosis from CXR images in an attempt to more closely understand the problems faced by researchers when dealing with those datasets, and how to mitigate some of them.


<img src="https://i.imgur.com/B8yLDXA.png" alt="drawing" width="300"/>

*Samples of chest X-Rays taken from the datasets used in this paper. Each image is labeled COVID-19 positive or not. Some datasets present extra classes, such as viral and bacterial pneumonia.*

<img src="https://i.imgur.com/FoZVpQH.png" alt="drawing" width="400"/>

*Distribution of maximum similarities between the images of the COVID-19 Radiography Database using pixel-wise similarity. The purple dashed line is the threshold chosen by our algorithm to select the images to be removed. Only pairs with maximum similarities close to 1 are shown in the graph.*

<img src="https://i.imgur.com/UIf4hCi.png" alt="drawing" width="600"/>

*Model accuracies on the COVID-19 Radiography Database for different amounts of training samples available (proportional to the whole target training dataset), using both random intializations and pre-training on each of the other two datasets. The shaded areas indicate a range of one standard deviation, estimated with 5-fold cross-validation.*


## Abstract

> As urgency over the coronavirus disease 2019 (COVID-19) increased, many datasets with chest radiography (CXR) and chest computed tomography (CT) images emerged aiming at the detection and prognostication of COVID-19. Over the last two years, thousands of studies have been published, reporting promising results. However, a deeper analysis of the datasets and the methods employed reveal issues that may hamper conclu-
sions and practical applicability. We investigate three major datasets commonly used in these studies, detect problems related to the existence of duplicates, address the specificity of classes within those datasets, and propose a way to perform external validation via cross-dataset evaluation. Our
guidelines and findings contribute towards a trustworthy application of machine learning in the context of image-based diagnosis, as well as offer a
more accurate assessment of models applied to the prognostication of diseases using image datasets and pave the way towards models that can be relied upon in the real world.

## Acknowledgments

* Research supported with Cloud TPUs from Google's TPU Research Cloud (TRC).
* Weights & Biases for providing free accounts for students.

## Authors

João Marcos Cardoso da Silva (@JoaoMarcosCSilva)

Pedro Martelleto (@PedroMartelleto)

We would like to specially thank Moacir A. Ponti (@maponti) for helping us and supervising the whole process.