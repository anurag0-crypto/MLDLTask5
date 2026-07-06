# CIFAR-10: ANN vs CNN Comparative Analysis

A hands-on comparison of a fully-connected neural network (ANN) and a convolutional neural network (CNN) on the CIFAR-10 image dataset, built with TensorFlow/Keras.

## Description

CIFAR-10 has 60,000 small color photos (32x32 pixels) split across 10 categories — airplane, automobile, bird, cat, deer, dog, frog, horse, ship, truck. This project trains two different neural networks on the same data, under the same conditions (15 epochs, same batch size, same train/validation/test split), and compares how well each one learns to classify the images.

## Results

| Model | Parameters | Training Time | Test Accuracy |
|-------|-----------|---------------|----------------|
| ANN (fully-connected) | 1,738,890 | 172s | 43.28% |
| CNN (convolutional) | 319,178 | 622s | **72.40%** |

The CNN ends up **29 percentage points more accurate**, despite having **5.4x fewer parameters**. It also wins on every single one of the 10 classes.

## Why the CNN wins

The ANN has to flatten each image into a flat list of numbers before it can look at it, which throws away all information about which pixels are next to which. The CNN looks at the image as an actual 2D grid, using small filters that slide across it and pick up on edges, textures, and shapes — the same features regardless of where they appear in the image. That's why it learns faster and generalizes better, even with far fewer parameters.

## What's in this repo

- `CIFAR10_ANN_vs_CNN_Comparative_Analysis.ipynb` — the full notebook: data exploration, both models, training curves, confusion matrices, per-class results, and a written conclusion.
- `CIFAR10_ANN_vs_CNN_Comparative_Analysis.html` — a read-only version you can open in any browser, no Jupyter needed.

## Running it yourself

1. Install the requirements:
   ```
   pip install tensorflow scikit-learn pandas matplotlib seaborn
   ```
2. Open the notebook in Jupyter, VS Code, or Google Colab.
3. Run all cells. CIFAR-10 downloads automatically the first time via `tf.keras.datasets.cifar10`.

## Possible next steps

- Add data augmentation (flips, crops, rotations) to improve the CNN further.
- Try a deeper CNN with batch normalization, or a known architecture like ResNet.
- Use transfer learning from a model pretrained on ImageNet.
