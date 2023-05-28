---
title: "Automated breast cancer diagnosis"
icon: "https://i.imgur.com/GD1LCTG.png"
date: 2023-01-01
draft: false
project_tags: ["AI", "DFKI", "Pytorch", "DL"]
summary: "A deep learning model that detects breast cancer + an interactive web interface with explainable AI"
weight: 1
---

<div>
<video src="https://github.com/PedroMartelleto/Breast-Cancer-dBM/assets/35240934/8536a58d-6c88-440a-91b6-3b9212577af9" autoplay="true" loop="true"></video>
</div>

## About

This project is open-source, and <a href="https://github.com/PedroMartelleto/Breast-Cancer-dBM">the code is available on Github</a>.

The core idea of this project is to revisit the breast cancer classification in order to identify potential so called "digital biomarkers" (dBM). These biomarkers describe parts of the input/features (e.g. a certain regions of the US image) that show a high correlation with target classes. In the field of breast cancer classification we have an obvious BM, namely the cancer itself. Other than that, other parts of the input could pose a high risk for breast cancer or occur as a side effect of breast cancer. Many medical issues show such second order indicators, which are not directly part of the disease itself but connected.

Using breast cancer classification as an example, the task is to set up a complete ML pipeline that could be integrated into an actual application. Especially in the medical field, explainable AI (ExAI) is of high relevance. Therefore, in addition to classifying the images, your task is to highlight and "explain" your models findings. 
