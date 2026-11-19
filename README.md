# Brain CT Hemorrhage Detection

A university machine learning project that classifies brain CT images as **Normal** or **Hemorrhage**. The notebook explores image characteristics, applies a shared preprocessing pipeline, compares traditional machine learning models with CNN experiments, and provides an interactive upload-and-predict demonstration using a linear SVM.

## Project contents

- `notebooks/Brain_CT_Hemorrhage_Detection.ipynb` — cleaned, shareable notebook with exploratory analysis, preprocessing, model training, evaluation, and prediction interface.
- `documentation/Project_Summary.md` — concise technical summary.

## Dataset

The notebook was developed with a local dataset of 200 PNG images, balanced across 100 Normal and 100 Hemorrhage labels. Dataset files and archives are excluded from this repository; add the dataset locally in the expected `dataset/` layout before running the notebook:

```text
dataset/
├── labels.csv
└── head_ct/
    └── head_ct/
        ├── 000.png
        └── ...
```

## Workflow

1. Inspect labels, sample images, image dimensions, pixel intensities, and class balance.
2. Convert scans to grayscale and resize proportionally to fit a 128 × 128 canvas, centered with zero padding.
3. Normalize pixel values for CNN input. Flatten and standardize pixels for traditional classifiers.
4. Use a stratified 80/20 train/test split (random state 42).
5. Compare Logistic Regression, linear SVM, RBF SVM, an RBF grid-search experiment, and CNN variants.

## Results

On the notebook's 40-image test split, the linear SVM reached **85% accuracy**, Logistic Regression and the untuned RBF SVM each reached **82.5%**, and the grid-search RBF SVM reached **60%**. The linear SVM's five-fold cross-validation mean on the training partition was **77.5%**; this is separate from test accuracy.

The notebook contains inconsistent saved CNN test results, and the augmentation experiment has no recorded test score. See the report for details. Results are preliminary and based on a small dataset.

## Running the notebook

Install the notebook dependencies used in the project: Python, NumPy, Pandas, Matplotlib, Seaborn, OpenCV, scikit-learn, TensorFlow/Keras, Pillow, and ipywidgets. Open `Brian CT.ipynb` in Jupyter after placing the dataset in the expected location. The notebook expects `archive.zip` in the working directory for its dataset extraction cells, or you can place the dataset directly in the expected `dataset/` layout. Some cells install packages; review those cells for your environment before running.

## Important note

This is an academic experimental project, not a clinically validated diagnostic system. It has not been externally validated and must not be used to make medical decisions.
