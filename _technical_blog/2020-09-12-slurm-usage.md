---
title: 'Slurm tips'
tags:
  - Slurm
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
- seff
- sstat

## Job Submission example 1

```bash
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
sleep 120  # run your script here
echo "Finished `date`" 
```

## Slurm status 

### Quesion: 

We know that slurm has three status: `allocated`, `mix` and `idle`. But what type resources do these status mean? CPU, GPU or RAM? What status it would be if CPU is run out but GPU and RAM are still available?

Answer: 

From my practice I found that the status for gpu partition depends on the use of GPU resource. In a gpu node, there are 4 gpus lets say. Then if 4 gpus are ran out, then the state becomes `allocated`. If 2 gpus are run, and the state is `mix`, if no gpus are run, the state is `idle`.

RAM can not be ran out at all, because default: MaxRAMPercent = 98.0%

### Question: 

In `cpus-per-task`, what does `cpus` mean? thread or proceesor? 

Answer:

> CPU (CR_CPU): CPU as a consumable resource.
> No notion of sockets, cores, or threads.
> On a multi-core system CPUs will be cores.
> On a multi-core/hyperthread system CPUs will be threads.
> On a single-core systems CPUs are CPUs. ;-)
---from [slurm website](https://slurm.schedmd.com/cons_res.html)


## Slurm sbatch exclude nodes or node list
https://bioinfocore.com/unix/slurm-sbatch-exclude-nodes-or-node-list/


