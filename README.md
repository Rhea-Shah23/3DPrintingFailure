# 3D Printing Failure Detection: Comparative Analysis Using Deep Learning

**Author:** Rhea Shah  
**Affiliation:** Illinois Mathematics & Science Academy  

---

## Project Overview

Additive manufacturing, commonly known as 3D printing, has the potential to revolutionize industries through rapid prototyping and customized production. However, it remains vulnerable to a wide range of defects that compromise structural integrity and product quality. This research presents a deep learning-based foundation for real-time detection of 3D printing failures, with the goal of enabling autonomous quality control systems.

---

## Research Focus

- **Objective:** Detect failures during the 3D printing process using image-based deep learning.
- **Dataset:** Modified CAXTON dataset, consisting of 10,000 curated images (7,455 successful, 2,545 failures).
- **Approach:** Comparative analysis of six deep learning models; feature extraction with logistic regression.

---

## Dataset Overview

- **Source:** CAXTON dataset
- **Modification:** Subset selection, failure label generation, de-duplication
- **Issues Addressed:**
  - Inconsistent labeling
  - Unjustified preprocessing
  - Unrealistic parameter constraints

---

## Models Evaluated

1. ResNet18 (Pretrained & Standard)
2. ResNet50 (Pretrained & Standard)
3. Vision Transformer (ViT)
4. Swin Transformer

All models were trained under the same conditions using:
- Learning rate: 0.00001
- Batch size: 32
- Epochs: 10
- Augmentation: ColorJitter
- Framework: PyTorch
- Hardware: NVIDIA T4 GPU

---

## Experiment 1: Model Comparison

| Model                 | Accuracy | Loss | Precision | Recall |
|-----------------------|----------|------|-----------|--------|
| ResNet18 (Pretrained) | 0.89     | 0.32 | 0.99      | 0.45   |
| ResNet18              | 0.88     | 0.31 | 0.99      | 0.48   |
| ResNet50 (Pretrained) | 0.89     | 0.30 | 0.91      | 0.55   |
| ResNet50              | 0.89     | 0.33 | 0.97      | 0.48   |
| Vision Transformer    | 0.86     | 0.54 | 0.83      | 0.39   |
| Swin Transformer      | 0.87     | 0.51 | 0.80      | 0.43   |

**Key Insight:** Pretrained ResNet50 outperformed all others, achieving 89% accuracy and highest recall.

---

## Experiment 2: Feature Extraction with Logistic Regression

| Approach             | Accuracy | Loss | Precision | Recall | Trainable Params |
|----------------------|----------|------|-----------|--------|------------------|
| Full ResNet18 Model  | 0.89     | 0.32 | 0.99      | 0.45   | 11.7 Million     |
| Feature Extraction   | 0.88     | 4.16 | 0.92      | 0.48   | 513              |

**Conclusion:** Feature extraction recovered nearly full performance at a fraction of the computational cost.

---

## Implementation Details

- **Data Preprocessing:** Normalization using dataset-specific mean and standard deviation.
- **Augmentation:** ColorJitter for lighting and color balance variability.
- **Optimizer:** Adam with StepLR scheduler.
- **Training Duration:** 10 epochs for each model.

---

## Limitations

- Class imbalance in the dataset
- Use of binary classification may oversimplify real-world failure types
- Domain-specific variability not captured (printer type, material, etc.)

---

## Future Work

- Address class imbalance with resampling or cost-sensitive learning
- Extend classification to multi-class failure modes
- Incorporate sensor data (e.g., temperature, acoustic signals) for multimodal learning
- Develop real-time correction mechanisms during the print process

---

## Citation

If referencing this work, please cite:

```bibtex
@misc{shah2024_3dprinting,
  title={3D Printing Failure Detection: Comparative Analysis Using Deep Learning},
  author={Rhea Shah},
  year={2024},
  note={Independent Research},
  url={https://github.com/your-repo-link}
}
```

---

## Acknowledgments

This research was completed under the mentorship of Mr. Andrew Alini and Mr. Asa Harbin. Special thanks to the Illinois Mathematics & Science Academy’s Student Research and Inquiry program for supporting this independent project.

---

## Resources

- CAXTON Dataset: [Original Study](https://www.nature.com/articles/s41467-022-31985-y)
