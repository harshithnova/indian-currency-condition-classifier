# Indian Currency Note Condition Classification Using AI

## Project Overview

This project uses deep learning to classify Indian currency notes into three condition categories: **Crisp, Worn, and Damaged**. The model predicts the condition of a currency note from an image and provides the predicted class along with a confidence score.

The project explores Convolutional Neural Networks (CNNs) and transfer learning for automated currency note condition classification, inspired by the fitness assessment performed by banknote sorting systems.

## Objectives

- Classify currency note images into Crisp, Worn, and Damaged categories.
- Build a custom CNN from scratch.
- Compare the custom CNN with MobileNetV2 using transfer learning.
- Evaluate models using accuracy, precision, recall, F1-score, and confusion matrices.
- Use Grad-CAM to understand which image regions influence predictions.
- Develop an image-upload demo that displays the predicted condition and confidence score.

## Dataset

The validated dataset is organized into three classes:

- **Crisp:** Clean or lightly circulated notes.
- **Worn:** Notes showing signs of circulation, fading, or creasing.
- **Damaged:** Notes with more severe physical damage.

The dataset is stored in Google Drive and divided into training, validation, and test sets.

```text
Dataset_v2/
├── train/
│   ├── Crisp/
│   ├── Damaged/
│   └── Worn/
├── val/
│   ├── Crisp/
│   ├── Damaged/
│   └── Worn/
└── test/
    ├── Crisp/
    ├── Damaged/
    └── Worn/
```

Images are resized to 128 × 128 pixels for model training. Data augmentation is used to help improve generalization.

The dataset was checked for near-duplicate images and inconsistent labels before the final split. The test set is kept separate from model training.

**Note:** The dataset is not included in this repository. Access and use depend on the original dataset's sharing permissions.

## Models

### 1. Custom CNN

A convolutional neural network built from scratch using TensorFlow and Keras. The architecture includes convolutional layers, batch normalization, max pooling, global average pooling, dropout, and a three-class softmax output layer.

### 2. MobileNetV2

A pretrained MobileNetV2 model adapted for three-class classification. Transfer learning is used first, followed by fine-tuning selected upper layers.

Both models are evaluated on the same test set for comparison.

## Initial Custom CNN Results

The custom CNN achieved the following baseline results:

| Metric | Result |
|---|---:|
| Test accuracy | 83.7% |
| Macro F1-score | 0.839 |
| Best validation accuracy | 94.4% |
| Crisp test accuracy | 100% (60/60) |
| Damaged/Worn combined accuracy | 75.8% |
| Accuracy on evaluated unseen Damaged/Worn notes | 59.4% |
| Model parameters | 102,595 |

The model performs well on the Crisp test images but has greater difficulty distinguishing Damaged notes from Worn notes.

These are baseline results. The custom CNN will be compared with MobileNetV2 using the same evaluation protocol.

## Evaluation and Explainability

The project evaluation includes:

- Test accuracy and macro F1-score.
- Per-class precision, recall, and F1-score.
- Confusion matrices.
- Training and validation accuracy/loss curves.
- Analysis of misclassified test images.
- Grad-CAM visualizations to inspect regions influencing predictions.
- Comparison of the custom CNN and MobileNetV2.

Only completed experiments and verified results will be reported as final results.

## Limitations

The dataset contains images captured under different conditions. Crisp images are primarily wide, clean scans, whereas many Worn and Damaged images are handheld photographs with varied backgrounds.

As a result, the model may learn image-source or background patterns in addition to actual currency condition. The lower accuracy on evaluated unseen Damaged/Worn notes highlights the need for more diverse images of physically different notes.

This project is an academic prototype and is not a replacement for certified banknote fitness inspection systems.

## Technologies Used

- Python
- Google Colab
- TensorFlow and Keras
- NumPy
- Matplotlib
- Scikit-learn
- MobileNetV2
- Grad-CAM

## Project Structure

```text
indian-currency-condition-classifier/
├── README.md
├── currency_condition_classifier.ipynb
├── results/
└── models/
```

The notebook contains the model development and evaluation workflow. The `results/` and `models/` folders can contain selected plots, evaluation outputs, and saved model files when available.


## Future Work

- Improve recognition of Damaged versus Worn notes.
- Evaluate generalization using more independently photographed notes.
- Investigate background-related shortcuts using Grad-CAM.
- Compare the custom CNN and MobileNetV2 using the same evaluation protocol.
- Improve the image-upload demo for easier testing.

## Disclaimer

This project is developed for educational and research purposes. Predictions are based on image patterns learned from the available dataset and should not be treated as official currency fitness decisions.
