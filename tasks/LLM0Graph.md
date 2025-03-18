---
id: 20250318124642-methodology
aliases:
  - Methodology
tags: []
---

# Model Name 


We focus on Text-Attribute Graphs. 

Overall framework

Given a pre-trained GNN, how can we adopt it onto the various downstream tasks, i.e., node-level, edge-level, and graph-level. 

Leverage LLMs to generate pesudo-labels for the downstream tasks. 
With these generated labels, we train the pr-trained GNN to adopt to the downstream tasks.

Novelty:
    1. Transfer Learning 
    2. Unified framework that can handle both node-level, edge-level, and graph-level tasks.
    3. Theoretical contribution. (optional)



## Methodology 

1. Pretrain Stage:
    
    GFT [1] without Tree Vocabulary. 
    Integrate node, edge, and graph level tasks for pre-train.

   Output: a GNN  

2. Test Time Training Stage:
    
    With a pretrained-GNN, we aim to conduct test-time training to adopt the pretrained-GNN on the downstream tasks. 
    
    Step 1: Leverage GNNs to generate task node embeddings.
    Step 2: Cluster the task node embeddings into |C| clusters. Here C is the classes.
    Step 3: We select nearest and farest node for each cluster, based on the distance with the centroid. (Active Node Selection)
    Step 4: With these selected nodes, we leverage LLMs to generate the pesudo-labels. (Same with LLMTTT).
    Step 5: Fine-tune pre-trained GNNs with these pesudo-labels.
    Step 6: Repeat 2-5 k times.  (K is a pre-defined hyper-parameters)
    Step 7: Downstream Tasks.

***Focus on LLMs methods***



Pesudo-Labels:
 1. Not guaranteed to be correct.
 2. Different with ground truth labels.





Tasks:
1. Read some test time training papers from NLP / CV. 
2. Think about the skeleton of the Introduction.
3. What kind of Insights we can provide to audiences. 
4. How to attract audiences, and let them feel your work is interesting.


 ..

# Minors


Test-time Training:
1. Class: pretrained Model [Large], output is embeddings. Attach a classifier (e.g., MLPs) at the end of the pre-trained model. In test-time training, we only fine-tune the parameters in the classifier.  Why? 
2. Full: fine-tune all, both pre-trained GNN and classifier.

Graph Foundation Models 
1. What is foundation model. NLP: texts => tokenizer => corresponding word embeddings.
2. Graph Foundation Model:  i) Structure heterogeneity; ii) Feature Heterogeneity.


# References                                                                                                                                                                       
[ 1] GFT: Graph Foundation Model with Transferable Tree Vocabulary.
2 One for All: Towards Traini.ng One Graph Model for All Classification Tasks.
[.3] Cost-Effective Label-free Node Classification with LLMs.
[4] Test-Time Training on Graphs with Large Language Models (LLMs).
[5] Label-free Node Classification on Graphs with Large Language Models (LLMS).
[6] Exploring the potential of large language models (llms) in learning on graphs.


Difference: this work merely study the OOD problem over a single graph. However, in our work, we pre-train on a set of datasets, and then test-time training on a different graph, i.e., the downstream tasks. 
