# LinkedIn Job Recommendation System

This repository contains the source code and documentation for a LinkedIn Job Recommendation System developed for **BT4221: Advanced Analytics with Big Data Technologies** at the National University of Singapore (AY 2024/25 Semester 2).

## Project Overview
Job seekers often struggle to identify roles that align with their current skills while lacking visibility into transitioning opportunities. This project builds and evaluates a personalized job recommendation system using both user profile information and job metadata.

We compare classical approaches against advanced Deep Learning models—specifically **Neural Collaborative Filtering (NCF)** and **Neural Matrix Factorization (NeuMF)**—to provide more accurate and relevant recommendations.

## System Architecture
The pipeline is designed to handle large-scale data and the absence of explicit user-job interaction logs:
* **Data Cleaning:** Removal of noisy metadata and parsing of stringified skill/experience lists into manageable arrays.
* **Pseudo-Interaction Generation:** Since real application data was unavailable, we generated "likes" (1) and "dislikes" (0) by calculating cosine similarity between user and job skill vectors using **Word2Vec** embeddings.
* **Feature Engineering:** Implementation of **LabelEncoding** for categorical identifiers and **Embedding Layers** to learn dense, trainable vector representations for users and jobs.

## Models Implemented
1.  **Content-Based Filtering (CBF):** Leverages TF-IDF and cosine similarity to match user job history and location with job descriptions.
2.  **User-Based Collaborative Filtering (UBCF):** Identifies similar users based on interaction patterns to suggest relevant roles.
3.  **Hybrid Filtering:** Integrates CBF and UBCF using a weighted average ($\alpha = 0.25$) to balance profile alignment with behavioral insights.
4.  **Neural Collaborative Filtering (NCF):** A deep learning architecture using Multi-Layer Perceptrons (MLP) to capture complex, non-linear user-job interactions.
5.  **Neural Matrix Factorization (NeuMF):** A state-of-the-art hybrid model combining Generalized Matrix Factorization (GMF) and MLP to model both linear and high-order latent features.


## Technical Challenges
* **Computational Overhead:** Managed high-dimensional similarity matrices by optimizing **PySpark** partitions and using **PCA** to reduce the dimensions of sparse user-job matrices.
* **Cold Start Problem:** Addressed the lack of historical logs through synthetic label generation based on embedding-driven similarity.
* **PySpark Lazy Evaluation:** Mitigated execution bottlenecks by periodically exporting intermediate DataFrames to CSV to reset the computation graph.

## Datasets
* **1.3M LinkedIn Job Postings (2024):** Sourced from Kaggle metadata.
* **3,600 LinkedIn User Profiles:** Sourced from research on profile authenticity and LLM generation.

## Contributors (Group 18)
* **CHANG WEI SONG** 
* **HENG HONG QUAN** 
* **LI XINYAN** 
* **NG ZHENG LENG BRYAN** 
* **WAN QIANHE** 

**Instructor:** Dr. Yeo Wee Kiang
**Date:** April 17, 2025
