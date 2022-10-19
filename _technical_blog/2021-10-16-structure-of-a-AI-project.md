---
title: 'Checklist for a complete deep learning python project'
tags:
  - python
  - Tutorial
---

Itemss you need to know for your AI project.

## Dataset
Check the quality of image and labels. 
Check if the shapes and spacings of images and labels are the same

## Collect the image statistics, summarize the dataset information
For non-anonymous images, use [this code](https://gist.github.com/Jingnan-Jia/98a36936f674cfd4e2feba56f34e654d) to collect patient information (sex, age, etc.). 
For anonymous images, use [this code](https://gist.github.com/Jingnan-Jia/c47c02de0e009466163245b61844d95a) to collect image information (spacing, size, labels).

## RUN
Check the image/labels before input them to networks. To see if they have the same spacing, shape, etc.

## MLFlow
1. Use database based mlflow server, which is faster than directory based mlflow.
  1. In linux shell: mlflow server --backend-store-uri=sqlite:///mlrunsdb.db --default-artifact-root=file:mlruns --host 0.0.0.0 --port 5000
  1. In python script: 
    ```python
    mlflow.set_tracking_uri("http://nodelogin02:5000")
    mlflow.set_experiment("lung_fun")
    ```
1. Assign a unique ID for each run.
```python
record_fpath = "results/record.log"
id = record_1st(record_fpath)
with mlflow.start_run(run_name=str(id), tags={"mlflow.note.content": args.remark}):
```

1. [Record cgpu information](https://github.com/Jingnan-Jia/ssc_scoring/blob/master/ssc_scoring/mymodules/tool.py).
```python
parser.add_argument("--hostname", type=str, default='None')
parser.add_argument("--jobid", type=str, default='None')
parser.add_argument("--outfile", type=str, default='None')


p1 = threading.Thread(target=record_cgpu_info, args=(args.outfile, ))
p1.start()
…
p1.do_run = False  # stop the thread
p1.join()
```
1. For ‘evaluate.py’:
```python
mlflow.set_tracking_uri("http://nodelogin02:5000")
experiment = mlflow.set_experiment("lung_fun")
args.reload_run_id = retrive_run_id(experiment=experiment, reload_jobid=args.reload_jobid)
mlflow.start_run(run_id=args.reload_run_id)  # find the trained run
mlflow.start_run(nested=True)  # start a nested run
```
1. Record FLOPs
1. Nested mlflow for Cross-fold validation
1. Record git version by automatic git for each experiments
1. Record time_load_batch, time_update_batch
1. Record train/valid/test loss, metrics, for each epoch
1. Record experiment ID, cpu_count, data_shuffle_seed, epochs, eval_id, batch_size, fold, gpu_name, hostname, loss_name, net_name, mode, net_parameters, outfile, pretrained, remark, workers, input_size, etc.
