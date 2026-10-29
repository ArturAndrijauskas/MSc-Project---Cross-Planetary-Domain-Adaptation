MSc Project: Cross-Planetary Domain Adaptation
Author: Artur Andrijauskas (Student ID: 220637107)
Institution: Queen Mary University of London
Supervisor: Ammar Yasir Naich

---

PROJECT OVERVIEW

This archive contains the complete supporting material, computational code, evaluation metrics, and visual assets for the MSc dissertation.

The project investigates whether pre-training an object detection model (YOLOv8) on a data-rich lunar source domain can successfully adapt to a data-scarce Martian target domain under a severe low-data regime.

---

DIRECTORY STRUCTURE & CONTENTS

1. Code/MScDissertationProject.ipynb
* The master Google Colab implementation notebook.
* Contains the complete pipeline: data engineering, dataset purification, 5-fold cross-validation harness generation, 
Lunar Expert training, scratch baseline training, transfer learning loops, and statistical testing.




2. Results/
* results_scratch_baseline.csv
* Final epoch performance logs (Precision, Recall, mAP50, mAP50-95)
for the control group trained completely from scratch across all 5 folds.


* results_transfer_learning.csv
* Final epoch performance logs for the experimental domain adaptation group
initialized with pre-trained lunar expert weights across all 5 folds.


* statistical_summary.csv
* Outputs of comparative statistical testing, including descriptive stats,
standard deviations, performance gains, and hypothesis testing values.




3. Visualisations/
* map50_fold_comparison.png
* High-resolution comparative bar chart displaying per-fold mAP50 scores
between the scratch baseline and transfer learning models (Report Figure 4).


* overall_metrics_summary.png
* Aggregated performance summary chart comparing Precision, Recall,
mAP50, and mAP50-95 with standard deviation error bars (Report Figure 5).



---

TECHNICAL ENVIRONMENT & DEPENDENCIES

Execution Platform : Google Colab (Cloud GPU Runtime)
Core Language      : Python 3.12
Deep Learning      : PyTorch, Torchvision, Ultralytics YOLOv8
Data Science       : Scikit-Learn (KFold cross-validation), Pandas, NumPy, SciPy
Visualization      : Matplotlib, Seaborn
Dataset Source     : Dynamically fetched via Kaggle API
Lunar Source: LU3M6TGT Dataset (riccardolagrassa/lu3m6tgt)
Martian Target: Martian/Lunar Dataset (lincolnzh/martianlunar-crater-detection-dataset)

---

VERIFICATION & REPRODUCIBILITY NOTES

The included Jupyter notebook incorporates automated sanity checks at the end of each development phase to guarantee data integrity:

Data Purity       : Programmatically filters out non-Martian images to prevent domain contamination.
Data Leakage      : Validates that training and validation splits across all 5 folds are strictly disjoint.
Artifact Integrity: Confirms that exported CSV logs and model weights are non-corrupted and bounded within valid metric ranges ([0.0, 1.0]).