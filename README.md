Comparison Study: Custom CNN vs MobileNetV2 (Transfer Learning)

This study evaluates two different deep learning approaches for the Banana Ripeness Classification problem using the Banana Ripeness Classification Dataset from Kaggle.

The dataset contains 4 classes:

overripe

ripe

rotten

unripe

Dataset counts:

Train: 11,793 images

Validation: 1,123 images

Test: 562 images

The experiment compares a scratch-built CNN and a pretrained MobileNetV2 model using Keras/TensorFlow.

1. Model Architectures
A. Custom CNN (Trained From Scratch)

3 convolutional blocks

Flatten layer + Dense(128) + Dropout

Total Parameters: 3.3M

All parameters trainable

Learns features from zero

B. MobileNetV2 (Transfer Learning)

Pretrained on ImageNet

Feature extractor frozen

Added layers:

GlobalAveragePooling

Dense(32)

Dense(4) output

Total Parameters: 2.29M

Trainable Parameters: 41K

Learns high-level features from pretrained backbone

2. Training Configuration
Setting	CNN	MobileNetV2
Image Size	128×128	160×160
Epochs	15	5
Optimizer	Adam	Adam
Loss	Categorical Crossentropy	Categorical Crossentropy
Augmentation	Standard	Standard
Batch Size	32	32
3. Results
A. Custom CNN Results

Validation Accuracy: 96.71% (best epoch)

Test Accuracy: 94.30%

Training behavior:

Slower convergence

Overfitting after ~10 epochs

Higher number of parameters

Entire network trained end-to-end

B. MobileNetV2 Results

Validation Accuracy: 96.97%

Test Accuracy: 97.15%

Training behavior:

Fast convergence (within 1–2 epochs)

No overfitting

Requires very few trainable parameters (only ~41k)

Leverages strong features from ImageNet

4. Quantitative Comparison
Metric	Custom CNN	MobileNetV2
Trainable Parameters	3.3M	41K
Total Parameters	3.3M	2.29M
Best Validation Accuracy	96.71%	96.97%
Test Accuracy	94.30%	97.15%
Convergence Speed	Slow	Fast
Overfitting	Medium	Very Low
Feature Quality	Basic	High-level pretrained features
5. Interpretation

MobileNetV2 significantly outperforms the custom CNN, despite training only 2% of the parameters.

Transfer learning provides robust feature extraction, improving accuracy by nearly +3% on the test dataset.

The custom CNN is more prone to overfitting and requires more epochs to stabilize.

MobileNetV2 is computationally lighter (41k trainable weights) and more suitable for deployment on mobile/edge devices.

The experiment demonstrates the effectiveness of transfer learning when dataset size and variability are sufficient.

6. Conclusion

The comparison clearly indicates that:

MobileNetV2 (Transfer Learning) is superior to a custom CNN

in terms of:

accuracy

training time

generalization

efficiency

robustness

For production-grade banana ripeness detection, MobileNetV2 is the recommended approach.
