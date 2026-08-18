# Bengali Handwritten Character Recognition with KNN

This project classifies handwritten Bengali characters from grayscale images using the K-Nearest Neighbors (KNN) algorithm.

The model recognizes all 46 classes in the included dataset: 11 Bengali vowels (স্বরবর্ণ) and 35 Bengali consonants (ব্যঞ্জনবর্ণ). For example, `ka` is labelled as `ক`, `kha` as `খ`, and `aa` as `আ`.

The 11 vowel labels are: `অ, আ, ই, ঈ, উ, ঊ, ঋ, এ, ঐ, ও, ঔ`.

The notebook covers image loading, pixel normalization, PCA, KNN model selection, evaluation, confusion-matrix analysis, nearest-neighbour inspection, and saving the final model.

## Dataset

The dataset is included in this repository inside the `data/` folder. It uses the real handwritten images from the BanglaNet-45 dataset, published under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).

Dataset citation:

> Nasir, M. N. U., Sultana, M., & Pranto, M. S. I. (2026). *BanglaNet-45: Handwritten Bangali Character Dataset* (Version 1). Mendeley Data. https://doi.org/10.17632/47fpd8js36.1

## Data folder structure

The image files are already included in the repository. Keep this structure unchanged when downloading, cloning, or sharing the project:

```text
bengali-vowel-knn/
├── bengali_vowel_knn_classifier.ipynb
└── data/
    ├── label_map.csv
    └── real_data/
        ├── train/
        │   ├── [class-folder-1]/
        │   │   ├── image_001.png
        │   │   └── ...
        │   └── ...
        └── test/
            ├── [class-folder-1]/
            │   ├── image_001.png
            │   └── ...
            └── ...
```

This included dataset uses romanized class folders, such as `ka`, `kha`, `aa`, and `ou`. The notebook maps every folder to its correct Bangla character automatically. Keep `label_map.csv` in `data/` only if you later replace the dataset with one that uses numeric class folders.

### Character labels in charts

The handwritten image itself is always the original Bengali character. However, some computers do not have a Bengali font that Matplotlib can display, so Bengali chart labels may appear as identical boxes or may look like the same character (for example, `ক`) even when the labels are different.

For this reason, the notebook displays the dataset's unique romanized class names in charts and predictions: `ka`, `kha`, `ga`, `aa`, `ii`, `ou`, and so on. Each name represents its own Bengali character class; for example, `ka` means `ক`, `kha` means `খ`, and `aa` means `আ`.

## How to get and run the project

No virtual environment, terminal commands, or separate requirements file is needed. The first notebook cell installs the required Python packages automatically in the active notebook kernel.

1. Download or clone the complete repository. If using a ZIP file, extract the whole folder without moving the notebook away from `data/`.
2. Open `bengali_vowel_knn_classifier.ipynb` in Jupyter Notebook, JupyterLab, or VS Code.
3. Confirm that the `data/` folder is beside the notebook, using the structure above.
4. Select **Run All** (or run the cells from top to bottom).
5. The first cell installs the packages; the remaining cells load the images, train the model, display results, and save the trained model.

If you use Google Colab, upload the entire project folder or clone the repository there before opening the notebook. Opening only the notebook file is not enough because the image files are stored in `data/`.

## Project workflow

1. Find the training and test image folders.
2. Select a balanced sample from all 46 character classes.
3. Convert each 32×32 image into pixel features and normalize values from 0–255 to 0–1.
4. Use PCA to reduce the number of features.
5. Test different K values with cross-validation.
6. Evaluate the best KNN model using accuracy, balanced accuracy, and a 46-class confusion matrix.
7. Inspect the nearest neighbours and one incorrect prediction.
8. Save the trained model.
