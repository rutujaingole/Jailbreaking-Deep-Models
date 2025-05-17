# Jailbreaking Deep Models: Adversarial Attacks on ImageNet-Classifiers

This repository contains the codebase for Deep Learning Project 3 (Spring 2025), which investigates the vulnerability of deep convolutional neural networks to adversarial attacks. The project systematically implements and analyzes Fast Gradient Sign Method (FGSM), Projected Gradient Descent (PGD), and localized patch-based attacks on the pretrained ResNet-34 model using a subset of the ImageNet-1K dataset.

## Project Overview

Modern neural networks, despite achieving high accuracy on standard benchmarks, remain susceptible to carefully crafted perturbations that are often imperceptible to humans. This project demonstrates how such attacks can significantly degrade model performance, even reducing ResNet-34's top-1 accuracy from 76% to 0% under PGD—while appearing visually unchanged.

Three attack strategies are explored:
- **FGSM**: A fast, single-step attack used as a baseline
- **PGD**: An iterative, stronger version of FGSM
- **Patch-based PGD**: A constrained version where only a 32×32 region is perturbed

In addition, the transferability of these attacks is evaluated on DenseNet-121 to assess cross-model generalization.

## Directory Structure
```
.
├── code/
│ ├── Project3_DL.ipynb # Main attack and evaluation notebook
├── figures/
│ ├── accuracy_barplot.png # Accuracy results under each attack
│ ├── adv_visuals_all_attacks.png # Original vs adversarial comparison with diff maps
│ └── Original and FGSM
| └── PGD and Patch
├── data/
│ └── TestDataSet.zip # Provided test dataset (or instructions to download)

```

## Main Libraries:
```
torch
torchvision
matplotlib
numpy

```

## Key Results

| Attack Type | Top-1 Accuracy (ResNet-34) | Top-5 Accuracy (ResNet-34) |
|-------------|-----------------------------|-----------------------------|
| Original    | 0.7600                      | 0.9420                      |
| FGSM        | 0.1040                      | 0.2460                      |
| PGD         | 0.0000                      | 0.0340                      |
| Patch       | 0.3700                      | 0.6940                      |

Transferability to DenseNet-121 was observed to be most effective for FGSM, with reduced impact for PGD and patch-based attacks.

## How to Run

All experiments are implemented using PyTorch. To reproduce results:
1. Open the `Project3_DL.ipynb` notebook in Colab or Jupyter.
2. Upload `TestDataSet.zip` to the working directory.
3. Run the notebook sequentially to generate adversarial examples, evaluate model accuracy, and visualize outputs.

## Notes

- The dataset is not included due to size constraints; please upload `TestDataSet.zip` manually if running on Colab.
- All images are normalized using ImageNet mean and standard deviation.
- Visualizations include pixel-wise difference maps (amplified ×10) to highlight imperceptible perturbations.

## Author
Rutuja Ingole
Net ID: rdi4221
This project was completed as part of the Deep Learning course at NYU, Spring 2025.
