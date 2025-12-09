## 🔧 1. Model Architectures
A. Custom CNN (Trained From Scratch)

3 Convolutional + MaxPooling blocks

Flatten → Dense(128) → Dropout → Dense(4)

Total Parameters: 3,305,156

Learns all features directly from dataset

B. MobileNetV2 (Transfer Learning)

Pretrained on ImageNet

Freezes base model

Adds: GlobalAveragePooling → Dense(32) → Dense(4)

Total Parameters: 2,299,108

Trainable Parameters: Only 41,124

Uses high-quality pretrained feature extractor

## ⚙️ 2. Training Configuration
Setting	Custom CNN	MobileNetV2
Image Size	128×128	160×160
Epochs	15	5
Trainable Params	3.3M	41K
Optimizer	Adam	Adam
Loss	Categorical Crossentropy	Categorical Crossentropy
Batch Size	32	32
## 📊 3. Results
Custom CNN

Validation Accuracy: 96.71%

Test Accuracy: 94.30%

Good learning capability but slower convergence

Mild overfitting after 10 epochs

MobileNetV2

Validation Accuracy: 96.97%

Test Accuracy: 97.15%

Faster convergence (1–2 epochs)

Strong generalization and minimal overfitting

Extremely small number of trainable parameters

## 📈 4. Quantitative Comparison
Metric	Custom CNN	MobileNetV2
Total Parameters	3.3M	2.29M
Trainable Parameters	3.3M	41K
Best Validation Accuracy	96.71%	96.97%
Test Accuracy	94.30%	97.15%
Convergence Speed	Slow	Fast
Overfitting Risk	Medium	Low
Feature Quality	Basic	High-level
## 🧐 5. Interpretation

MobileNetV2 outperforms the Custom CNN in accuracy, speed, and generalization.

Transfer learning achieves higher performance with fewer trainable parameters.

Custom CNN shows good learning but requires more epochs and is prone to overfitting.

MobileNetV2 is more suitable for deployment on mobile/edge devices.

## 🏁 6. Conclusion

MobileNetV2 (Transfer Learning) is the superior model for banana ripeness detection due to:

Higher test accuracy

Faster training

Fewer trainable parameters

Better generalization

Lower overfitting risk

For production use, MobileNetV2 is recommended.

## 📦 Repository Contents
