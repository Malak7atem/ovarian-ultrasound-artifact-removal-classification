# Segmentation-Guided Inpainting and Imbalance-Aware Learning for Robust Ovarian Tumor Classification in Ultrasound

Research project on reducing visual artifacts and class-imbalance effects in deep-learning-based ovarian tumor classification from ultrasound images.

## Overview

Ultrasound images can contain non-biological annotations—such as calipers, measurement lines, arrows, and text—that may introduce shortcut correlations during model training. Severe class imbalance can also reduce sensitivity to underrepresented tumor categories.

This work investigates a pipeline that combines:

1. **Artifact segmentation:** U-Net is used to identify measurement overlays and other artifacts.
2. **Segmentation-guided inpainting:** Predicted artifact masks guide a pre-trained LaMa model to reconstruct affected regions.
3. **Imbalance-aware learning:** Class rebalancing and training-time augmentation/optimization strategies are used to improve learning across underrepresented classes.
4. **Classification:** Convolutional neural-network backbones, including EfficientNet, are evaluated for eight-class ovarian tumor classification.

## Dataset

Experiments use the **MMOTU-2D** dataset, containing 2,500 transvaginal ultrasound images across eight ovarian tumor classes.

Dataset source: [MMOTU: Multi-Modality Ovarian Tumor Ultrasound Dataset](https://doi.org/10.6084/m9.figshare.25058690)

Please obtain the dataset from its original source and follow its license and usage terms. The dataset is not included in this repository.

## Reported Results

| Experiment | Result |
|---|---:|
| U-Net artifact segmentation validation Dice | 90.61% |
| U-Net artifact segmentation validation mIoU | 83.00% |
| LaMa inpainting configuration, single-run Top-1 accuracy | 80.38% |
| LaMa inpainting configuration, single-run Top-2 accuracy | 89.98% |
| Full pipeline (Approach I), five-seed Top-1 accuracy | 75.99 ± 2.21% |
| Full pipeline (Approach I), five-seed Macro-F1 | 70.50 ± 2.66% |

**Important:** The 80.38% result is from the single-run inpainting-method comparison. The 75.99 ± 2.21% result is the five-seed evaluation of the full Approach I pipeline. These are different experimental settings and should not be presented as directly interchangeable.

## Methods and Tools

- Python and PyTorch
- U-Net and DeepLabV3 for artifact segmentation experiments
- LaMa (Large Mask Inpainting) for image reconstruction
- EfficientNet-B0 and EfficientNet-B2, among other evaluated backbones
- Weighted sampling and augmentation strategies, including Mixup and Random Erasing
- Cross-entropy with label smoothing and Soft-F1 in the evaluated imbalance-aware variant

## Repository Contents

```text
.
├── paper/
│   └── ovarian_tumor_classification_paper.pdf
└── README.md
```

This repository currently shares the research paper. Source code, trained weights, and dataset files are not included unless added separately.

## Authors

Alaa Khaled, Malak Hatem, Malak Eissa, Sara Abozeid, and Sahar Selim

Center for Informatics Science (CIS), School of Information Technology and Computer Science, Nile University, Egypt.

## Citation

If you use or refer to this work, please cite the paper:

> Khaled, A., Hatem, M., Eissa, M., Abozeid, S., & Selim, S. *Segmentation-Guided Inpainting and Imbalance-Aware Learning for Robust Ovarian Tumor Classification in Ultrasound.*

Add the final publication details (venue, year, DOI, or proceedings link) when they are available.

## Scope and Limitations

The reported experiments are conducted on the MMOTU-2D dataset under the evaluation setup described in the paper. The results do not establish clinical readiness. Further validation on independent, prospectively collected data is needed before clinical use.
