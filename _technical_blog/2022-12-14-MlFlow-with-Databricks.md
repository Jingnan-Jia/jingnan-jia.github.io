---
title: MLflow FAQ
tags:
  - Knowledge
  - Tools
---

# MLflow with Databricks

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

# MLflow, restore runs/experiments
## restore experiments
In python [2]:
```
# restore experiments
from mlflow import MlflowClient

def print_experiment_info(experiment):
    print("Name: {}".format(experiment.name))
    print("Experiment Id: {}".format(experiment.experiment_id))
    print("Lifecycle_stage: {}".format(experiment.lifecycle_stage))

# Create and delete an experiment
client = MlflowClient()
experiment_id = client.create_experiment("New Experiment")
client.delete_experiment(experiment_id)

# Examine the deleted experiment details.
experiment = client.get_experiment(experiment_id)
print_experiment_info(experiment)
print("--")

# Restore the experiment and fetch its info
client.restore_experiment(experiment_id)
experiment = client.get_experiment(experiment_id)
print_experiment_info(experiment)
```
## restore runs 
In python [2]:
```

from mlflow import MlflowClient

# Create a run under the default experiment (whose id is '0').
client = MlflowClient()
experiment_id = "0"
run = client.create_run(experiment_id)
run_id = run.info.run_id
print("run_id: {}; lifecycle_stage: {}".format(run_id, run.info.lifecycle_stage))
client.delete_run(run_id)
del_run = client.get_run(run_id)
print("run_id: {}; lifecycle_stage: {}".format(run_id, del_run.info.lifecycle_stage))
client.restore_run(run_id)
rest_run = client.get_run(run_id)
print("run_id: {}; lifecycle_stage: {}".format(run_id, res_run.info.lifecycle_stage))

```
# MLflow, how to delete the runs/experiments Permanently? 

In CLI [1]:
```
mlflow experiments delete [OPTIONS]
mlflow experiments restore [OPTIONS]
mlflow experiments search [OPTIONS]

mlflow gc [OPTIONS]  # delete the experiments permanently 
```

In CLI [1]:
```
mlflow runs delete [OPTIONS]
mlflow runs restore [OPTIONS]  # --run-id <run_id> 
mlflow runs list [OPTIONS]

mlflow gc [OPTIONS]  # delete the experiments permanently 
```

References:
1. https://mlflow.org/docs/latest/cli.html#mlflow-gc
2. https://mlflow.org/docs/latest/python_api/mlflow.client.html#mlflow.client.MlflowClient.restore_run