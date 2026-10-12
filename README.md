# QuishGuard

A lightweight multimodal framework for detecting **quishing** (QR-code phishing) attacks, combining a visual branch (`MobileViTv2_100`) and a semantic branch (`DistilBERT-base-uncased`) with feature-level fusion.

## Overview
QuishGuard detects malicious QR codes by jointly analysing:
- **Visual branch:** QR-image structure via a fine-tuned `MobileViTv2_100` → 512-D embedding
- **Semantic branch:** decoded + canonicalized URL via a fine-tuned `DistilBERT-base-uncased` → 768-D embedding
- **Fusion:** the two embeddings are concatenated (1280-D) and classified by a fully connected network (FCNN)

## Repository Contents
| Path | Description |
|------|-------------|
| `dataset_1m_combined_balanced.csv` | Balanced ~1M URL corpus used to generate the QR dataset |
| `Qr/` | Rendered QR-code images |
| `.gitattributes` | Git LFS / attributes configuration |

## Dataset
- ~1,000,000 balanced benign/malicious samples
- URLs rendered as QR codes (qrcode library; error-correction level L, box size 10, 4-module quiet zone, 256×256 px)
- 11 categories (benign + 10 attack types); stratified 65/15/20 train/val/test split (seed 42)

## Usage
1. Clone the repository.
2. (Dataset) `dataset_1m_combined_balanced.csv` contains the URL corpus; QR images are under `Qr/`.
3. Source code for training and evaluation is available on request (see Contact).

## Citation
If you use this dataset or framework, please cite:
