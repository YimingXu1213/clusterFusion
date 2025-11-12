# CLUSTERFUSION: Hybrid Clustering with Embedding Guidance and LLM Adaptation

This repository contains datasets and experimental results for the paper **"CLUSTERFUSION: Hybrid Clustering with Embedding Guidance and LLM Adaptation"**.

**Paper link**: arXiv link to be added soon.

---

## Datasets

This repository includes the following datasets:

### Benchmark Datasets
- **Bank77**: Banking intent classification dataset (obtain from original source)
- **CLINC**: Intent classification dataset (obtain from original source)  
- **Tweet**: Social media clustering dataset (obtain from original source)

*Note: Please refer to the original papers for these benchmark datasets and their licensing terms.*

### Cleaned CLINC Dataset
- **File**: `datasets/clinicSmallCleaned_4472samples_150topics.csv`
- **Description**: Manually cleaned version of the original CLINC data. We identified and removed mislabeled records to improve data quality.
- **Correction Notes**: `datasets/clinicSmall_correction_notes.csv` documents all mislabeled records found in the original dataset.

### OpenAI Codex Dataset (New)
- **File**: `datasets/codex_406samples_26topics.csv`  
- **Description**: YouTube comments collected and labelled from the [OpenAI Codex demo video](https://www.youtube.com/watch?v=FUq9qRwrDrI) (collected before June 2025)
- **Data Processing**:
  - Removed sensitive information
  - Split multi-topic reviews into single-topic comments
  - Retained only comments about the announced product and its announcement
  - Removed follow-up discussions under specific comments
  - Removed duplicate entries
- **License**: CC BY 4.0

---

## Data Format

Each dataset CSV file contains the following columns:
- `task`: Dataset name (if applicable)
- `comment`: Raw text comment/document
- `topic`: Ground-truth topic/cluster label
- `pred_topic`: Predicted topic (in result files only)

---

## Results

The `results/` folder contains experimental outputs for each dataset. Each dataset has 5 subfolders corresponding to different input sorting strategies:

### Sorting Methods
- **`sorted_gt/`**: ClusterFusion with oracle ordering (sorted by ground-truth topics)
- **`sorted_pred_cos/`**: ClusterFusion sorted by cosine similarity to the first comment in the sample
- **`sorted_pred_euc/`**: ClusterFusion sorted by Euclidean distance to the first comment in the sample
- **`sorted_pred_K-means/`**: ClusterFusion sorted by K-means predicted clusters
- **`unsorted/`**: ClusterFusion without sorting. For the unsorted version, we randomized the input data. This is important since the CLINIC dataset is originally sorted by ground-truth topics. We've randomized all datasets to remove the built-in ordering that comes with the data.

### Result Files
- Each subfolder contains 5 CSV files (`_1.csv` through `_5.csv`), representing 5 independent experimental runs under the same configuration
- Each result file contains the predicted topics (`pred_topic` column) alongside the original data
- For evaluation metrics and methodology details, please refer to the paper

---

## Citation

*Citation information will be updated upon arXiv publication.*

---

## Contact

For questions or issues regarding this repository, please open an issue or refer to the paper for author contact information.
