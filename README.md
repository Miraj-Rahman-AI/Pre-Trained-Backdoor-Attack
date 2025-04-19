# Pre-Trained-Backdoor-Attack

**Pre-Trained Backdoor Attack** is a research-grade implementation aimed at exploring a critical and emerging threat vector in modern machine learning pipelines—**backdoor attacks embedded in pre-trained encoders**. This project demonstrates how adversaries can inject stealthy triggers during the pre-training phase of an encoder model and then exploit these vulnerabilities in downstream tasks without altering the architecture or parameters of target models.

## 🌐 Overview

Pre-trained models have become a cornerstone of transfer learning and few-shot learning due to their versatility and performance. However, this paradigm shift also opens up novel attack surfaces. Unlike traditional backdoor attacks that target end-to-end classifiers, **this project focuses on compromising the encoder itself**, making it possible to affect *any* future model or task that uses the compromised encoder. This form of attack is stealthy, generalizable, and transferable.

The attack methodology leverages task-agnostic trigger embedding into the encoder’s feature space during pre-training. Once embedded, the encoder behaves normally on clean data but exhibits malicious behavior when presented with specific trigger patterns—effectively "flipping" class predictions or causing targeted misclassifications.

## 📁 Repository Structure
```Pre-Trained-Backdoor-Attack/ 
│ ├── 📂 clip/
│ ├── clip.py # CLIP model wrapper 
│ ├── model.py # CLIP model architecture 
│ └── simple_tokenizer.py # Tokenizer for text input
│ ├── 📂 datasets/
│ ├── backdoor_dataset.py # Base class for poisoned datasets 
│ ├── cifar10_dataset.py # CIFAR-10 dataset handler 
│ ├── gtsrb_dataset.py # GTSRB dataset handler 
│ ├── stl10_dataset.py # STL10 dataset handler 
│ └── svhn_dataset.py # SVHN dataset handler 
│ ├── 📂 evaluation/
│ └── nn_classifier.py # Evaluation using nearest neighbor classifier 
│ ├── 📂 log/
│ └── [Dataset Logs] # Evaluation results for clean and backdoor settings 
│ ├── 📂 models/
│ └── [Trained Models] # Saved encoder and classifier models 
│ ├── 📂 references/
│ └── [Papers, Notes] # Related academic literature 
│ ├── 📂 scripts/
│ └── [Utilities] # Helper scripts for setup and processing 
│ ├── 📂 trigger/
│ └── [Trigger Files] # Backdoor trigger generator (e.g., patch/pattern-based) 
│ ├── bdencoder.py # Backdoored encoder logic 
├── pretraining_encoder.py # Encoder pre-training with backdoor injection 
├── training_downstream_classifier.py # Train classifier on downstream task 
├── zero_shot.py # Zero-shot evaluation of poisoned encoder 
└── README.md # Project documentation
```


## 🎯 Key Features

- ✅ **Encoder-Level Backdoor Injection**: Embed stealthy triggers during encoder pretraining.
- 🔁 **Transferability**: Poisoned encoder affects multiple downstream tasks without retraining.
- 📦 **Dataset Diversity**: Supports CIFAR-10, STL10, GTSRB, and SVHN for comparative evaluation.
- 🧠 **Zero-shot and Supervised Evaluation**: Validate both transfer learning and fully trained classifiers.
- 📊 **Log-supported Reproducibility**: All experimental outputs are preserved under the `log/` directory.
- 🔐 **Security Relevance**: Simulates real-world attack scenarios targeting pre-trained model hubs.

## 📜 Theoretical Motivation

This project is motivated by the increasing reliance on public model hubs and transfer learning in real-world AI applications. While these practices accelerate development, they also introduce a **supply-chain vulnerability**: if the pre-trained encoder is compromised, the integrity of all subsequent uses of that encoder is jeopardized. This is especially concerning for:

- Federated Learning Systems  
- Multi-task and Multi-modal Learning  
- Model-as-a-Service (MaaS) platforms  
- Zero-shot Learning Pipelines  

Our implementation draws insights from state-of-the-art adversarial ML research, including stealthy poisoning, feature-space manipulation, and stealth-preserving optimization.

## ⚙️ Installation and Setup

### 1. Clone the Repository

```bash
git clone https://github.com/Miraj-Rahman-AI/Pre-Trained-Backdoor-Attack.git
cd Pre-Trained-Backdoor-Attack
