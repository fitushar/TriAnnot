# TriAnnot

<div align="center">
<p align="center">
  <img src="https://github.com/fitushar/TriAnnot/blob/main/assert/Triannot_logo.png" alt="Triannot_logo" width="500">
</p>

**Tri-stage AI-Based Annotation Consensus Framework for Lung Cancer Screening**

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)
[![Docker](https://img.shields.io/badge/Docker-ft42%2Fpins%3Alatest-2496ED?logo=docker)](https://hub.docker.com/r/ft42/pins)
[![Python](https://img.shields.io/badge/Python-3.9+-green.svg)](https://python.org)
[![Medical Imaging](https://img.shields.io/badge/Medical-Imaging-red.svg)](https://simpleitk.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.8.0-orange.svg)](https://pytorch.org)
[![MONAI](https://img.shields.io/badge/MONAI-1.4.0-blue.svg)](https://monai.io)
[![PiNS](https://img.shields.io/badge/PiNS-1.0.0-blue.svg)](https://github.com/fitushar/PiNS)
[![CaNA](https://img.shields.io/badge/CaNA-1.0.0-cyan.svg)](https://github.com/fitushar/CaNA)
</div>

<p align="center">
  <img src="https://github.com/fitushar/TriAnnot/blob/main/assert/Triannot_workflow.png" alt="Triannot_lworkflow" width="1200">
</p>



# Abstract
TriAnnot is a framework for pulmonary nodule annotation that combines three complementary stages:

* **Detection (Teacher–Student Agreement):** Multiple detectors are organized in a teacher–student setup to generate candidates and filter false positives through agreement.
* **Classification:** Each candidate is assigned a malignancy score from independent classifiers.
* **Segmentation and Morphology:** Segmentation-derived features (size, shape, margin) are extracted to provide structural annotation.

Each candidate receives three independent annotation scores (detector agreement score, classifier score, and morphology score). These scores can be used individually or in combination to support downstream tasks such as risk modeling, benchmarking, and automated consensus annotation.

**Key Features**

* Teacher–student detector agreement to ensure robust candidate generation.
* Independent classifier scoring for malignancy assessment.
* Morphology features from segmentation for quantitative annotation.
* Multi-score output per candidate to enable reproducible benchmarking.
* **plug & play** and changable modules
