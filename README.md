# Skip-Connected Reverse Distillation for Robust One-Class Anomaly Detection
![CVPR 2025 Workshop](https://img.shields.io/badge/CVPR%202025-Workshop-red)
![License](https://img.shields.io/github/license/pej0918/SK-RD4AD)
![Python](https://img.shields.io/badge/python-3.9+-blue)
> 📣 Accepted at **CVPR 2025 Workshop (VAND 3.0)**  
> 🔧 Official PyTorch implementation of our paper, SK-RD4AD.

## 📖 Introduction

SK-RD4AD (Skip-Connected Reverse Distillation for Anomaly Detection) introduces a novel approach to one-class anomaly detection by leveraging non-corresponding skip connections within a Reverse Knowledge Distillation (KD) framework. This architecture addresses the deep feature loss issue prevalent in traditional models by effectively preserving multi-scale feature information, thereby enhancing anomaly localization and detection performance.

## 🔥 Key Features
- **🔗 Non-Corresponding Skip Connections**: Ensures both fine-grained and high-level structural information retention.
- **🚀 State-of-the-Art Performance**: Achieves +3.5% AUROC improvement over RD4AD on MVTec-AD, VisA, and VAD datasets.
- **🌐 Generalization Capability**: Robust against challenging anomaly types, including the difficult Transistor class in MVTec-AD.


## 📂 Model Overview
**SK-RD4AD** enhances the **RD4AD** framework by tackling **information loss** in deep layers. By introducing **non-corresponding skip connections**, it effectively preserves **multi-scale features**, allowing **fine-grained details** to influence **deeper layers**, significantly boosting **anomaly detection performance**.


![Architecture Diagram](https://github.com/pej0918/pej0918.github.io/blob/main/assets/imgs/image_skrd4ad.png)

## ⚙️ Experiment Settings

### 🧪 Installation
```bash
pip install -r requirements.txt
```

### 📁 Dataset Preparation
Download the MVTec, VAD and VisA datasets from:
- [MVTec AD Dataset](https://www.mvtec.com/company/research/datasets/mvtec-ad/)
- [Valeo Anomaly Dataset (VAD)](https://drive.google.com/file/d/1LbHHJHCdkvhzVqekAIRdWjBWaBHxPjuu/view/)
- [visA Dataset](https://github.com/amazon-science/spot-diff)

### 🏃 Train and Test the Model
To train and evaluate the model, use the appropriate script depending on the dataset.

The following command is for training and evaluating the model on **MVTec-AD** :
```bash
python main.py \
    --epochs 200 \
    --res 3 \
    --learning_rate 0.005 \
    --batch_size 16 \
    --seed 111 \
    --class all \
    --seg 1 \
    --print_epoch 10 \
    --data_path /home/user/mvtec/ \
    --save_path /home/user/anomaly_checkpoints/skipconnection/ \
    --print_loss 1 \
    --net wide_res50 \
    --L2 0
```
## 📈 Performance Highlights
SK-RD4AD consistently outperforms the baseline RD4AD model across multiple benchmark datasets, demonstrating its robust anomaly detection capabilities. The integration of **non-corresponding skip connections** not only enhances **multi-scale feature retention** but also significantly boosts **anomaly localization** performance : 

### MVTec-AD Dataset Performance
| Category     | RD4AD (Pixel AUROC/AUPRO) | SK-RD4AD (Pixel AUROC/AUPRO)   |
|--------------|----------------------------|--------------------------------|
| Carpet       | 98.9 / 97.0                | **99.2 / 97.7**                |
| Bottle       | 98.7 / 96.6                | **98.8 / 96.9**                |
| Hazelnut     | 98.9 / 95.5                | **99.1 / 96.2**                |
| Leather      | 99.4 / 99.1                | **99.6 / 99.2**                |
| **Total Avg**| 97.8 / 93.9                | **98.06 / 94.69**              |

### Valeo Anomaly Dataset (VAD) Performance
| Setting   | Baseline AUROC | SK-RD4AD AUROC |
|-----------|----------------|----------------|
| One-Class | 84.5           | **87.0**       |

### VisA Dataset Performance
| Category     | RD4AD (Pixel AUROC / AUPRO) | SK-RD4AD (Pixel AUROC / AUPRO) |
|--------------|-----------------------------|--------------------------------|
| PCB1         | 99.6 / 43.2                 | 99.6 / **93.7**                |
| PCB2         | 98.3 / 46.4                 | 98.3 / **89.2**                |
| PCB3         | 99.3 / 80.3                 | 98.3 / **90.3**                |
| PCB4         | 98.2 / 72.2                 | **98.6 / 89.0**                |
| Pipe Fryum   | 99.1 / 68.3                 | 99.1 / **94.8**                |
| **Total Avg** | 97.8 / 70.9                 | **98.5 / 92.1**                |


## 🖼️ Visualization
<p align="center">
  <img src="https://github.com/user-attachments/assets/b2fe4e4b-6a4c-4c86-8caa-ebef8da92dd8" alt="figg3" width="45%">
  <img src="https://github.com/user-attachments/assets/dbbd9d8a-f70a-4a8f-9a9b-49e2f95ed4be" alt="ffig2" width="45%">

</p>

The visualization results demonstrate **the effectiveness of the SK-RD4AD model in detecting anomalies**. The anomaly maps highlight areas where the model identifies potential defects, using red and yellow hues to indicate regions of high confidence. The overlaid images combine the original images with the anomaly maps, clearly showing the detected anomalies' locations.

## 🎯 Conclusion
SK-RD4AD addresses the challenge of deep feature loss in anomaly detection by introducing **non-corresponding skip connections** within a reverse distillation framework.  
This design improves **multi-scale feature retention** and enhances the model's ability to detect **subtle and diverse anomalies**.  
Tested across industrial benchmarks, it shows consistent improvements over RD4AD, making it a **robust and effective solution for real-world anomaly detection tasks**.

## 📚 Citation

```
TBD
```

