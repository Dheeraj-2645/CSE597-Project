# FACMIC: Federated Adaptive CLIP Model for Medical Image Classification

## Introduction
This repository contains the official implementation of the paper **"FACMIC: Federated Adaptive CLIP Model for Medical Image Classification"**. FACMIC extends the Contrastive Language-Image Pretraining (CLIP) model to the federated learning domain, enabling privacy-preserving medical image classification.

The key features of FACMIC include:
- A **Feature Attention Module** to refine task-specific features in medical images.
- A **Domain Adaptation Mechanism** using Maximum Mean Discrepancy (MMD) loss to handle non-IID data distribution across clients.
- Support for federated learning across multiple clients, with MRI brain tumor classification as the primary use case.

This implementation uses the **Brain Tumor dataset**, categorizing MRI scans into four classes: glioma tumor, meningioma tumor, pituitary tumor, and no tumor.

---

## Dependencies
Ensure the following packages are installed. You can install them directly using the provided `requirements.txt` file.

```bash
openai-clip
numpy==1.26.4
opencv-python==4.9.0.80
openpyxl==3.1.2
Pillow==11.0.0
scikit-image==0.21.0
scikit-learn==1.6.0
scipy==1.14.1
tqdm==4.66.1
torch
torchvision
```


To install dependencies, run:
```bash
pip install -r requirements.txt
```
## Steps to Run the Code

### 1. Clone the Repository
Clone the repository to your local machine:

```bash
git clone git@github.com:Dheeraj-2645/CSE597-Project.git
```

### 2. Prepare the Dataset
The project uses the Brain Tumor dataset, which is already structured for federated learning across 4 clients. The dataset includes:

glioma tumor
meningioma tumor
pituitary tumor
no tumor
You can download the dataset from the following link: [Brain Tumor Dataset](https://drive.google.com/drive/folders/1__sN_2857bnhjJdEoBR48dweXRqM_ZsA?usp=sharing)

Ensure the dataset follows the structure below:

```bash
./data/BrainTumor/
    client_0/
      glioma_tumor/
      meningioma_tumor/
      no_tumor/
      pituitary_tumor/
    client_1/
    client_2/
    client_3/
```

### 3. Run the Code
You can reproduce the results from the paper by running the main script:

```bash
python main.py --dataset BrainTumor --test_envs 3
```
#### Command Line Arguments
- `--dataset`: The dataset to use. Default is `BrainTumor`.
- `--test_envs`: Specifies which client(s) will be used as the test environment(s). Default is `[3]` (Client 3).

---

### 4. Monitor Training
Logs during training will display the following:
- **Training and Validation Accuracy** for each client.
- **Test Accuracy and Balanced Accuracy** for each test site.

The results will also be saved to the `./results/` directory:
- `Global_Acc7.csv`: Test accuracies for all epochs.
- `Global_bacc7.csv`: Balanced accuracies for all epochs.


## Results

The FACMIC framework achieves state-of-the-art performance on the **Brain Tumor dataset**. Final results include:

- **Accuracy (Acc)** and **Balanced Accuracy (Bacc)** for each test site.
- Average metrics across all clients, matching the results reported in the paper.

For reference, results from the paper are as follows:

| Metric            | Average Accuracy (Acc) 
|--------------------|-------------------------|
| **Paper**         | 0.8274                  |
| **This Run**      | 0.7819 |
