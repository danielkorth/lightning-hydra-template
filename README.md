## 📌  Introduction

This is a fork of the [lightning-hydra-template](https://github.com/ashleve/lightning-hydra-template) adjusted to my needs. This template is supposed to make it easier to start deep learning project following a streamlined process as outlined by Prof. Niessner in  [this](https://x.com/MattNiessner/status/1441027241870118913) tweet. I also aim to incorporate other best practices when deemed useful. Please check out the orginal template for more information on faetures and how to use it.

I tried to create a basic checklist to aid the development workflow for your deep learning project - however note that this is always highly linear and you will often have to deviate from it. 

---

## Stage 1 - Overfitting
In this stage, we are trying to verify that the data loading and basic optimization works. It is crucial to start with a simple setup to identify potential issues early on.
- [ ] Implement DataModule (+ config file)
- [ ] Implement LightningModule (+ config file)
- [ ] Create config file in experiment/overfit_single (disable any fancy features)
- [ ] Overfit on a single sample (loss should go to 0)
- [ ] Create config file in experiment/overfit_batch (disable any fancy features)
- [ ] Overfit on a batch (loss should still go to 0)

```bash
# to run the overfitting experiments
python src/train.py experiment=overfit_single/${experiment_name}
python src/train.py experiment=overfit_batch/${experiment_name}
```

## Stage 2 - Fast Experimentation
Now that the basic opitmization works, it is time to start some experiments. This stage is all about fast iterations and identifying the most promising directions. Generally, stay with a small model architecture at this stage (see also this [tweet](https://x.com/gabriberton/status/1797274445213466786)).
- [ ] Make Training loop fast (identify bottlenecks)
```bash
python src/train.py experiment=train/${experiment_name} debug=simple_profiler
```
- [ ] Add additional metrics to log
- [ ] Run experiments with different hyperparameters (kill early if not promising)

## Stage 3 - Scaling up
Finally, it is time to scale up the model size and add more advanced features to your model to help with generalization.

---

This should provide you with a high-level overview of how to approach a Deep Learning Project. Obviously, this is a very non-linear process and you will deviate from it - regard it as a rough guideline.

**DELETE EVERYTHING ABOVE FOR YOUR PROJECT**

______________________________________________________________________

<div align="center">

# Your Project Name

<a href="https://pytorch.org/get-started/locally/"><img alt="PyTorch" src="https://img.shields.io/badge/PyTorch-ee4c2c?logo=pytorch&logoColor=white"></a>
<a href="https://pytorchlightning.ai/"><img alt="Lightning" src="https://img.shields.io/badge/-Lightning-792ee5?logo=pytorchlightning&logoColor=white"></a>
<a href="https://hydra.cc/"><img alt="Config: Hydra" src="https://img.shields.io/badge/Config-Hydra-89b8cd"></a>
<a href="https://github.com/ashleve/lightning-hydra-template"><img alt="Template" src="https://img.shields.io/badge/-Lightning--Hydra--Template-017F2F?style=flat&logo=github&labelColor=gray"></a><br>
[![Paper](http://img.shields.io/badge/paper-arxiv.1001.2234-B31B1B.svg)](https://www.nature.com/articles/nature14539)
[![Conference](http://img.shields.io/badge/AnyConference-year-4b44ce.svg)](https://papers.nips.cc/paper/2020)

</div>

## Description

What it does

## Installation

#### Pip

```bash
# clone project
git clone https://github.com/YourGithubName/your-repo-name
cd your-repo-name

# [OPTIONAL] create conda environment
conda create -n myenv python=3.9
conda activate myenv

# install pytorch according to instructions
# https://pytorch.org/get-started/

# install requirements
pip install -r requirements.txt
```

#### Conda

```bash
# clone project
git clone https://github.com/YourGithubName/your-repo-name
cd your-repo-name

# create conda environment and install dependencies
conda env create -f environment.yaml -n myenv

# activate conda environment
conda activate myenv
```

## How to run

Train model with default configuration

```bash
# train on CPU
python src/train.py trainer=cpu

# train on GPU
python src/train.py trainer=gpu
```

Train model with chosen experiment configuration from [configs/experiment/](configs/experiment/)

```bash
python src/train.py experiment=experiment_name.yaml
```

You can override any parameter from command line like this

```bash
python src/train.py trainer.max_epochs=20 data.batch_size=64
```
