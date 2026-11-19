# Brain CT Hemorrhage Detection Project Summary

## Project
Binary image classification of 200 PNG brain CT images into Normal (label 0) and Hemorrhage (label 1), with 100 images per class.

## Implemented workflow
- Inspected labels, sample images, image dimensions, intensity histograms, per-image statistics, and feature correlations.
- Converted images to grayscale, resized proportionally into 128 × 128 images with centered zero padding, and normalized pixels to [0, 1].
- Used a stratified 80/20 split (random_state=42): 160 training and 40 test images.
- Flattened and standardized images for Logistic Regression and linear/RBF SVMs; trained CNNs on one-channel image tensors.
- Added an RBF SVM grid search, early stopping, one augmentation experiment, and a lower learning-rate CNN experiment.
- Built an ipywidgets upload/prediction flow using the linear SVM and saved scaler.

## Results
- Logistic Regression: 82.5% test accuracy.
- Linear SVM: 85.0% test accuracy; class-wise hemorrhage recall 0.90.
- RBF SVM: 82.5% test accuracy.
- Grid-search RBF SVM: 59.375% mean training-partition CV accuracy and 60% test accuracy.
- Linear SVM 5-fold CV mean: 77.5% (distinct from test accuracy).
- CNN records conflict: summary table reports baseline 70% and reduced-learning-rate 50%, while detailed evaluation cells include baseline 50% and reduced-learning-rate 62.5%. Augmentation has no saved test score.

## Limitations
Only 200 images; external validation and patient-level independence are not documented; image provenance is unclear; CNN output records conflict; upload preprocessing differs from dataset resizing. This is an educational prototype, not a clinically validated system.

See `Brain_CT_Hemorrhage_Detection_Report.docx` for the full 12-chapter report.
