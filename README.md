# 🔤 Handwritten Alphabet Recognition with CNN

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
![Python](https://img.shields.io/badge/Python-3.8+-blue.svg)
![TensorFlow](https://img.shields.io/badge/TensorFlow-2.x-orange.svg)
[![Kaggle](https://img.shields.io/badge/Kaggle-View%20Notebook-20BEFF?logo=kaggle)](https://www.kaggle.com/code/abdelrahmanabdelalem/handwritten-english-recognition-on-2-diff-datasets)

> A robust deep learning solution for recognizing handwritten uppercase English letters (A-Z) with **99% accuracy** on the primary dataset and **~92% cross-dataset generalization**.

<grok-card data-id="e056de" data-type="image_card" data-arg-size="LARGE"></grok-card>

---
**Domain Shift** refers to the performance drop that occurs when a model trained on one dataset is evaluated on another dataset with different visual properties.  
This project focuses on mitigating domain shift to ensure strong generalization across different handwriting styles.

## 🎯 Project Highlights

- ✨ **99%+ Accuracy** on primary A-Z handwriting dataset
- 🔄 **91-92% Generalization** to completely different handwriting styles
- 🚀 **Lightweight Model** with only 137K parameters
- 🛠️ **Production-Ready** preprocessing and inference pipeline
- 📊 **Comprehensive Evaluation** with detailed error analysis

<grok-card data-id="d659f7" data-type="image_card" data-arg-size="LARGE"></grok-card>

---

## 📊 Datasets

### Primary Dataset (Training)
**[A-Z Handwritten Alphabets in CSV](https://www.kaggle.com/datasets/sachinpatel21/az-handwritten-alphabets-in-csv-format)**
- 372,450 grayscale 28×28 images
- 26 unbalanced classes (A-Z uppercase)
- Source: NIST and NMIST databases

### Secondary Dataset (Generalization Testing)
**[English Handwritten Characters](https://www.kaggle.com/datasets/dhruvildave/english-handwritten-characters-dataset)**
- ~3,400 uppercase samples
- Different styles, backgrounds, and thicknesses
-  unbalanced classes (0-9 , A-Z)

<grok-card data-id="b302d7" data-type="image_card" data-arg-size="LARGE"></grok-card>

---

## 🏗️ Model Architecture

**Lightweight CNN** optimized for handwritten character recognition:

<grok-card data-id="84b432" data-type="image_card" data-arg-size="LARGE"></grok-card>

### Structure
- **Input**: 28×28×1 grayscale images
- **3 Convolutional Blocks**: 32 → 64 → 128 filters with ReLU, Dropout (0.25), MaxPooling
- **Dense Layers**: 64 → 128 → 26 (Softmax)
- **Total Parameters**: 137,178
- **Optimizer**: Adam | **Loss**: Categorical Crossentropy

<grok-card data-id="3ae404" data-type="image_card" data-arg-size="LARGE"></grok-card>

---

## 📈 Performance

<grok-card data-id="491ad3" data-type="image_card" data-arg-size="LARGE"></grok-card>

### Primary Dataset Results
| Metric | Score |
|--------|-------|
| **Training Accuracy** | 99.12% |
| **Validation Accuracy** | 99.08% |
| **Test Accuracy** | 99.05% |
| **Training Time** | ~5 min (GPU) |

<grok-card data-id="34d02a" data-type="image_card" data-arg-size="LARGE"></grok-card>

### Cross-Dataset Generalization

Progressive improvement through domain adaptation:

| Technique                         | Accuracy | Gain |
|----------------------------------|----------|------|
| Baseline (no adaptation)         | 15.03%   | —    |
| + Advanced Preprocessing         | 66.36%   | +51.33% |
| + Fine-tuning (3 stages)         | 83.43%   | +17.07% |
| + Data Augmentation              | **91.75%** | **+8.32%** |


<grok-card data-id="f97513" data-type="image_card" data-arg-size="LARGE"></grok-card>

### Common Confusion Pairs
- **O ↔ Q** (circular shapes)
- **I ↔ L** (vertical lines)
- **M ↔ N** (zigzag patterns)
- **S ↔ Z** (curves vs angles)

<grok-card data-id="523e04" data-type="image_card" data-arg-size="LARGE"></grok-card>

---

## 🔬 Technical Approach

### Advanced Preprocessing
1. **Denoising** - Remove image noise
2. **CLAHE** - Contrast enhancement
3. **Auto-Inversion** - Handle white/black backgrounds
4. **Adaptive Thresholding** - Better binarization
5. **Morphological Operations** - Clean edges
6. **Character Centering** - Consistent positioning
7. **Normalization** - Scale to [0,1]

### Data Augmentation
- Rotation (±1°)
- Width/Height shifts (± 0.1)
- Zoom (± 0.1)
- Shear transformations

### 3-Stage Fine-Tuning
1. **Stage 1**: Train last Dense layers only
2. **Stage 2**: Unfreeze last Conv block + Dense
3. **Stage 3**: Fine-tune entire model with very low LR

<grok-card data-id="f0838d" data-type="image_card" data-arg-size="LARGE"></grok-card>

---

## 🚀 Quick Start

### Installation
```bash
pip install tensorflow numpy pandas matplotlib seaborn opencv-python scikit-learn
```

### Download Datasets
```bash
kaggle datasets download -d sachinpatel21/az-handwritten-alphabets-in-csv-format
kaggle datasets download -d dhruvildave/english-handwritten-characters-dataset
```

### Run Notebook
Open the [Kaggle Notebook](https://www.kaggle.com/code/abdelrahmanabdelalem/handwritten-english-recognition-on-2-diff-datasets) and click **"Copy & Edit"** to run on your own.

---

## 💡 Key Takeaways

✅ **Domain Shift Challenge**: Models trained on one dataset may struggle on different styles  
✅ **Preprocessing Matters**: Advanced preprocessing led to a **+51% absolute accuracy improvement** over the baseline.
✅ **Fine-Tuning Works**: Progressive fine-tuning contributed an additional **+17% gain**.  
✅ **Augmentation Helps**: Data augmentation provided final 1-2% boost  
✅ **Generalization is Key**: Testing on multiple datasets ensures robustness

---
## 🧠 Skills Demonstrated

- Deep Learning (CNNs)
- Domain Adaptation
- Computer Vision Preprocessing
- Model Fine-Tuning Strategies
- Data Augmentation
- Model Evaluation & Error Analysis


---

## 🤝 Contributing

Contributions are welcome! Feel free to:
- Report bugs or issues
- Suggest improvements
- Submit pull requests
- Share your results

---

## 📜 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

## 🙏 Acknowledgments

- **Datasets**: NIST, NMIST, and Kaggle contributors
- **Framework**: TensorFlow/Keras team
- **Inspiration**: Computer vision and deep learning community

---

## 📧 Contact

For questions or collaborations:
- **Kaggle**: [@abdelrahmanabdelalem](https://www.kaggle.com/abdelrahmanabdelalem)
- **GitHub**: [https://github.com/Abdo265]

---

<div align="center">

**⭐ Star this repo if you found it helpful!**

Made with ❤️ for the ML community

</div>
