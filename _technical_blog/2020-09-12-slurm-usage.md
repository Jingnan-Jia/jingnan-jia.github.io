---
title: 'Slurm usage'
tags:
  - slurm
  - Tutorial

---


# Frequently used commands

- scontrol show jobs [job id]
- scontrol show partition [queue]
- scontrol show nodes
- squeue
- sacct -j [job-id]
- scontrol hold job-id
- scontrol release job-id
- scancel job-id
- sbatch
- srun  --pty bash
- sinfo 
- sview

## Job Submission example 1
```bsh
#!/bin/bash 
#SBATCH --job-name=example
#SBATCH --output=output.txt
#SBATCH --ntasks=1 
#SBATCH --cpus-per-task=6
#SBATCH --mem-per-cpu=40G
#SBATCH --partition=gpu
#SBATCH --gres=gpu:1 
#SBATCH --time=0 

echo "on Hostname = $(hostname)"
echo "on GPU      = $CUDA_VISIBLE_DEVICES"
echo "@ $(date)"

conda activate py38
python Simple_try.py  
```

## Job Submission example 2
```bash
#!/bin/bash
#
#SBATCH -J slurm_example
#SBATCH -o example.output
# change to working directory default for SLURM
#SBATCH -D ./
# Mail all events
#SBATCH --mail-type=ALL
# set your email address
#SBATCH --mail-user your@email.address
# Request 8 hours run time
#SBATCH -t 8:0:0
# 
#SBATCH --mem=4000  #MB
#specify 2 cores
#SBATCH --ntasks-per-node=2

echo "start job SLURM `date`"
sleep 120
echo "Finished `date`" 
```

## Slurm status 
In a gpu node, there are 4 gpus lets say. Then if 4 gpus are ran out, then the state becomes allocated. If 2 gpus are run, and the state is mix, if no gpus are run, the state is idle.

