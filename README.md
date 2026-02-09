# CIFAR-10 Classifier (ICSSR Track 2) — 96.4% Test Accuracy

## Results Summary
| Model | Test Acc | Val Acc | Params |
|-------|----------|---------|---------|
| **Baseline CNN** | **78.7%** | 80.1% | 666K |
| **ResNet18 (TL)** | **96.4%** | **96.8%** | 11.2M |
| **Improvement** | **+22.5%** | +21.0% | - |

**metrics.json** contains full results.

## Technical Approach
### Baseline (SmallCNN from scratch)
- 3 conv blocks (32→64→128 filters)
- Adam (lr=1e-3), 15 epochs

### Improved (ResNet18 Transfer Learning)
1. **Phase 1**: Freeze backbone, train classifier (lr=3e-3)
2. **Phase 2**: Full fine-tune (lr=1e-4, cosine schedule)  
3. **Augmentation**: RandomCrop, Flip, ColorJitter
4. **Regularization**: Label smoothing (0.1), AdamW

## Evaluation
- **Train/Val/Test**: 45k/5k/10k (stratified split)
- **Metrics**: Accuracy, Confusion Matrix, Per-class F1
- **Seed**: 42 (reproducible)

## 🚀 Run Locally
Open `ICSSR.ipynb` in Google Colab (GPU) → Run all cells (~15 mins)

**Full notebook is end-to-end reproducible.**

