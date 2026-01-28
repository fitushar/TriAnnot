# Tri-Reader

<div align="center">


**Tri-Reader: An Open-Access, Multi-Stage AI Pipeline for First-Pass Lung Nodule Annotation in Screening CT**

[![License: CC BY-NC 4.0](https://img.shields.io/badge/License-CC%20BY--NC%204.0-lightgrey.svg)](https://creativecommons.org/licenses/by-nc/4.0/)
[![Docker](https://img.shields.io/badge/Docker-ft42%2Fpins%3Alatest-2496ED?logo=docker)](https://hub.docker.com/r/ft42/pins)
[![Python](https://img.shields.io/badge/Python-3.9+-green.svg)](https://python.org)
[![Medical Imaging](https://img.shields.io/badge/Medical-Imaging-red.svg)](https://simpleitk.org)
[![PyTorch](https://img.shields.io/badge/PyTorch-2.8.0-orange.svg)](https://pytorch.org)
[![MONAI](https://img.shields.io/badge/MONAI-1.4.0-blue.svg)](https://monai.io)
[![PiNS](https://img.shields.io/badge/PiNS-1.0.0-blue.svg)](https://github.com/fitushar/PiNS)
[![CaNA](https://img.shields.io/badge/CaNA-1.0.0-cyan.svg)](https://github.com/fitushar/CaNA)
</div>

Using multiple open-access models trained on public datasets, we developed Tri-Reader, a
comprehensive, freely available pipeline that integrates lung segmentation, nodule detection, and
malignancy classification into a unified tri-stage workflow. The pipeline is designed to
prioritize sensitivity while reducing the candidate burden for annotators. To ensure accuracy and
generalizability across diverse practices, we evaluated Tri-Reader on multiple internal and external
datasets as compared with expert annotations and dataset-provided reference standards 

### Citation Manuscript 

[![arXiv](https://img.shields.io/badge/arXiv-2405.04605-<color>.svg)](https://arxiv.org/pdf/2601.19380)

```ruby
@misc{tushar2026trireaderopenaccessmultistageai,
      title={Tri-Reader: An Open-Access, Multi-Stage AI Pipeline for First-Pass Lung Nodule Annotation in Screening CT}, 
      author={Fakrul Islam Tushar and Joseph Y. Lo},
      year={2026},
      eprint={2601.19380},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2601.19380}, 
}
```

**Tri-Reader** tri-stage workflow for first-pass lung nodule annotation in screening CT.
After lung segmentation (VISTA3D) removes extra-pulmonary candidates, Stage 1 performs consensus
CADe using two complementary detection models (CADe-ROIonly and the false-positive–aware
CADe-FPaware trained via strategic hard-negative mining); candidates detected by both are promoted
to confidence = 1.0. Stage 2 applies ensemble malignancy scoring to disagreement candidates using
two CADx classifiers trained on complementary distributions (DLCS24-CADxr50SWS and LUNA25-
CADxr50); candidates with an averaged $CADx ≥ 0.10$ are promoted (confidence = 0.5). Stage 3 retains
remaining candidates meeting $CADe ≥ 0.20$ (confidence = 0.2), yielding a single merged candidate list
with tiered confidence intended to reduce annotator workload while preserving sensitivity; an optional
rule-based NLP module can link report-derived descriptors to candidates when radiology reports are
available.





<p align="center">
  <img src="https://github.com/fitushar/TriAnnot/blob/main/assert/WorkflowDiagram.png" alt="Triannot_lworkflow" width="800">
</p>


**Below candidate review panel for SAMPLE_0124 (68-year-old; Intgmultiomics cohort, SAMPLE_0124.nii).**
The leftmost tile is the dataset-provided ground-truth nodule; the remaining tiles are additional candidates proposed by our pipeline. Each tile shows the axial CT slice (left) and a magnified ROI (right); the yellow square marks the candidate location. The header above each tile reports ANod (annotation-consensus score), CADx (malignancy probability), CADe (detector confidence), Lrg.ax (largest axis, mm), lobar location, and slice index. Frame color follows the cancer-risk scale shown in the bottom bar (<0.25, ≥0.25, ≥0.50, ≥0.75).

<p align="center">
  <img src="https://github.com/fitushar/TriAnnot/blob/main/assert/SAMPLE_0124_candidates.png" alt="SAMPLE_0124_candidates" width="1200">
</p>



## 🚀 Updates

- **[1] 09/30/2025** - 📢 Created Github and Huggingface repo
- **[2] 28/01/2025** - 📂 Mnauscript (Pre-print) [![arXiv](https://img.shields.io/badge/arXiv-2405.04605-<color>.svg)](https://arxiv.org/pdf/2601.19380)
- **[3]** - 📂 Public release of **19K NLST CT Annotations** ![Coming Soon](https://img.shields.io/badge/Status-Coming%20Soon-orange).
- **[4]** - 📂 Public release of **CT RATE Validation Dataset Annotations** ![Coming Soon](https://img.shields.io/badge/Status-Coming%20Soon-orange).
