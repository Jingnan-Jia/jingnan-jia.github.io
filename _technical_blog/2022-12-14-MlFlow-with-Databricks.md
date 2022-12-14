---
title: MLFlow with Databricks
tags:
  - Knowledge
  - Tools
---


Today I learnt how to use MLFlow in Databricks [1].

By the way, today I just found that MLFlow is released and maintained by Databricks! Databricks is so great!


This tutorial covers the following steps:

1. Import data from your local machine into the Databricks File System (DBFS)
1. Visualize the data using Seaborn and matplotlib
1. Run a parallel hyperparameter sweep to train machine learning models on the dataset
1. Explore the results of the hyperparameter sweep with **MLflow**
1. Register the best performing model in **MLflow**
1. Apply the registered model to another dataset using a Spark UDF
1. **Set up model serving for low-latency requests** (This is new to me!)


References:
1. https://docs.databricks.com/mlflow/end-to-end-example.html