# ViLongT5 • [![twitter](https://img.shields.io/twitter/url/https/shields.io.svg?style=social)](https://x.com/nicolayr_/status/1855348255153861026)
![](https://img.shields.io/badge/Python-3.8+-lightgreen.svg)
[![PRs welcome!](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]()
[![twitter](https://img.shields.io/twitter/url/https/shields.io.svg?style=social)](https://x.com/nicolayr_/status/1855348255153861026)

A pretrained [Transformer-based encoder-decoder model](https://arxiv.org/pdf/2112.07916.pdf) for the
multi-document text-summarization
task in Vietnamese language.
The code represents a non-framework implementation, which 
combines 
[flaxformer](https://github.com/google/flaxformer), 
[t5x](https://github.com/google-research/t5x)
and purely based on [JAX library](https://github.com/google/jax).

`ViLongT5` is trained on a large NewsCorpus of Vietnamese news texts.
We benchmark `ViLongT5` on multidocument text-summarization tasks,
Abstractive Text Summarization and Named Entity Recognition.
All the experiments are shown in our paper
**[Pre-training LongT5 for Vietnamese Mass-Media
Multi-document Summarization Task](https://link.springer.com/article/10.1007/s10958-024-07435-z)**


# Pretrained Models
**Vocabulary:**
[ViLongT5_vocab](sentencepiece/model/vietnam.vocab) / [training-script](sentencepiece/readme.md)

Model        | Gin File Location                                                                  | Checkpoint Location|
------------ | ---------------------------------------------------------------------------------- | -------------------|
ViLongT5-Large | [ViLongT5_large.gin](https://www.dropbox.com/s/nu3hgkz36zra3qq/config.gin?dl=1) | [ViLongt5-finetuned-large.tar.gz](https://www.dropbox.com/s/gl4vxpie7s3liqm/longt5-finetuned-vims-vmds-vlsp-large.tar.gz?dl=1) |

📄 Example scripts based on `Flaxformer` library for model: 
    [finetunning](usage/finetunning.md) / 
    [inferring](usage/inferring.md) / 
    [evaluating](usage/evaluating.md)

### Results

![image](https://user-images.githubusercontent.com/14871187/233701416-af11f6ff-40fd-4575-9727-fbb932cc76ed.png)

### Datasets
List of datasets utilized in experiments conduction:
- [NewsCorpus](https://github.com/binhvq/news-corpus)
- [VMDS](https://github.com/lupanh/VietnameseMDS)
- [ViMS](https://github.com/CLC-HCMUS/ViMs-Dataset)

# Installation

> **NOTE:** considering `GPU` as a computational device.
This project has been tested under the following [configuration](misc/nvidia-smi.txt)

* Python-3.8+
* List of the python packages at `dependencies.txt`
    * The [complete list of packages](misc/pip_freeze.txt) this project has been tested under `venv`.
* CUDA Compiler `nvcc`
    * [Installation details](https://docs.nvidia.com/cuda/cuda-installation-guide-linux/index.html)
* CuDNN toolkit `cudnn`
    * [Installation details](https://docs.nvidia.com/deeplearning/cudnn/install-guide/index.html)

### Local Installation

* Initialize virtual environment and install project dependencies:
```
virtualenv env --python=/usr/bin/python3.9`
pip install -r dependencies.txt
```
* [Re-install JAX with the related support of the GPU](usage/jax-gpu-support-tutorial.md).

### Kaggle Installation

For testing under [Kaggle](https://www.kaggle.com/), [there is a separted tutorial](usage/kaggle.md).

# Fine-tuning

* [Fine-tunning (`t5x` tutorial)](usage/finetunning.md)

We finetunning the model based on training part of the `vims+vmds+vlsp` training part as follows:
```
python -m t5x.train --gin_file="longt5_finetune_vims_vmds_vlsp_large.gin" --gin_search_paths='./configs'
```

# Inferring 
* [Inferring (`t5x` tutorial)](usage/inferring.md)

# Evaluation

For `vims+vmds+vlsp` (test part) is as follows:
```
python -m t5x.eval --gin_file="longt5_eval_vims_vmds_vlsp_large.gin" --gin_search_paths='./configs'
```

For `vlsp` (validation part) is as follows:
```
python -m t5x.eval --gin_file="configs/longt5_infer_vlsp_validation_large.gin" --gin_search_paths='./configs'
```

# References
```bibtex
@inproceedings{rusnachenko2023pretraining,
    title = "Pre-training {LongT5} for Vietnamese Mass-Media Multi-document Summarization Task",
    author = "Rusnachenko, Nicolay and Le, The Anh and Nguyen, Ngoc Diep",
    booktitle = "Proceedings of Artificial Intelligence and Natural Language",
    year = "2023"
}
```
