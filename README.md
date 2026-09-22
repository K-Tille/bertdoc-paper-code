# Model Testing Guide

This repository accompanies the paper “Evaluation of transformer-based relevance models for clinical information retrieval” 
and provides all resources required to reproduce and evaluate the experiments.

If you use this repository in your research, please cite the paper:

````markdown
@article{x,
  title        = {Evaluation of transformer-based relevance models for clinical information retrieval},
  author       = {Tille, Karsten and Toddenroth, Dennis and Ganslandt, Thomas},
  year         = {2026},
}
````

## Testing the Models

To evaluate the models, use the corresponding Dockerfiles:

Sentence Transformer: dockerfile_sentence (includes: all-mpnet-base-v2, med-mpnet-relevance-v1, med-mpnet-relevance-v1.1)

ColBERT: dockerfile_colbert (includes: colbert-ir/colbertv2.0, med-colbert-relevance-v1, med-colbert-relevance-v1.1)

Build and run the Docker image that matches the model series you want to test.


## Requirement for ColBERT (GPU)

The ColBERT model requires a GPU.

Make sure NVIDIA Docker (nvidia-container-toolkit) is installed and configured on your system.

Run the container with GPU support enabled:

1. Build => docker build -f dockerfile_colbert -t bertdoc_colbert:latest .
2. start => docker run --gpus all -p 7777:7777 bertdoc_colbert:latest
3. Look for a token for jupyter e.g. =>  http://127.0.0.1:7777/tree?token=2df1de0b1668d6811b09
4. run _complete_colbert_example.ipynb

## Requirement for Sentence Transformer (no GPU)

The Sentence Transformers dont need a GPU.

1. Build => docker build -f dockerfile_sentence -t bertdoc_sentence:latest .
2. Start => docker run -p 5555:5555 bertdoc_sentence:latest
3. Look for a token for jupyter e.g. =>  http://127.0.0.1:7777/tree?token=2df1de0b1668d6811b09
4. run _complete_sentence_transformer_example.ipynb


## Results in Notebooks

The evaluation results for all models are stored in:
__statistic_roc_boxplot.ipynb