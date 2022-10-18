---
title: 'Advanced usage of MLFlow'
date: 2022-8-10
tags:
  - Python packages
  - Tutorial
  - AI tools

---
MLflow is an open source platform to manage the ML lifecycle, including experimentation, reproducibility, deployment, and a central model registry. 

## The diffrence between MLFlow and other alternatives

## How to use it in you code?

- Use database based mlflow server.
    - In linux shell: mlflow server --backend-store-uri=sqlite:///mlrunsdb.db --default-artifact-root=file:mlruns --host 0.0.0.0 --port 5000
    - In python script: 
        - mlflow.set_tracking_uri("http://nodelogin02:5000")
        - mlflow.set_experiment("lung_fun")
- Assign a unique ID for each run.
    - record_fpath = "results/record.log"
    - id = record_1st(record_fpath)
    - with mlflow.start_run(run_name=str(id), tags={"mlflow.note.content": args.remark}):
- Record cgpu information.
    - parser.add_argument("--hostname", type=str, default='None')
    - parser.add_argument("--jobid", type=str, default='None')
    - parser.add_argument("--outfile", type=str, default='None')
    - p1 = threading.Thread(target=record_cgpu_info, args=(args.outfile, ))
    - p1.start()
    - …...
    - p1.do_run = False  # stop the thread
    - p1.join()
- For ‘evaluate.py’:
    - mlflow.set_tracking_uri("http://nodelogin02:5000")
    - experiment = mlflow.set_experiment("lung_fun")
    - args.reload_run_id = retrive_run_id(experiment=experiment, reload_jobid=args.reload_jobid)
    - mlflow.start_run(run_id=args.reload_run_id)  # find the trained run
    - mlflow.start_run(nested=True)  # start a nested run


- Record FLOPs
- Nested mlflow for Cross-fold validation
- Record git version by automatic git for each experiments
- Record time_load_batch, time_update_batch
- Record train/valid/test loss, metrics, for each epoch
- Record experiment ID, cpu_count, data_shuffle_seed, epochs, eval_id, batch_size, fold, gpu_name, hostname, loss_name, net_name, mode, net_parameters, outfile, pretrained, remark, workers, input_size, etc.


