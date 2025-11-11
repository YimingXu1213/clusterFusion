# CLUSTERFUSION: Hybrid Clustering with Embedding Guidance and LLM Adaptation

This is the repo the paper: CLUSTERFUSION: Hybrid Clustering with Embedding Guidance and LLM Adaptation

datasets/

    - clinicSmallCleaned_4472samples_150topics.csv -> this is the manual cleaned version of the original clinic data from Zhang et al. (2023). We removed the mis-labelled records documented in clinicSmall_correction_notes.csv

    - clinicSmall_correction_notes.csv -> documented the mis-labelled records for the original clinic data.

    - codex_406samples_26topics.csv -> data augmentation: remove sensitive information and split the multi-topic reviews to multiple 1 topic review. Only maintain those comments regarding the announced product and its announcement, remove the follow-up discussion under a specific comment. Remove duplicate results.

results/

    Under each dataset folder, there are 5 folders:
    - sorted_gt: Comments were sorted by ground-truth topics before being passed into the topic extractor.
    - unsorted: Comments were randomly shuffled before being passed into the topic extractor.
    - sorted_pred_K-means: Comments were sorted by predicted clusters from K-means before being passed into the topic extractor.
    - sorted_pred_cos: Comments were sorted by cosine similarity of their embeddings to the first comment, then passed into the topic extractor.
    - sorted_pred_euc: Comments were sorted by Euclidean distance of their embeddings to the first comment, then passed into the topic extractor.

