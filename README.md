# ViLongT5
[![PRs welcome!](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)]()

A pretrained Transformer-based encoder-decoder model for the
multi-document text-summarization
problem in Vietnamese language.
With [LongT5](https://github.com/google/flaxformer) original architecture
implementation,
ViLongT5 is trained on a large NewsCorpus of news Vietnamese texts.
We benchmark LongViT5 on multidocument text-summarization tasks,
Abstractive Text Summarization and Named Entity Recognition.
All the experiments are shown in our paper
**[Pre-training LongT5 for Vietnamese Mass-Media
Multi-document Summarization Task]()**


## Pretrained Models
**Vocabulary:**
[ViLongT5_vocab](sentencepiece-model/vietnam.vocab)

Model        | Gin File Location                                                                  | Checkpoint Location|
------------ | ---------------------------------------------------------------------------------- | -------------------|
ViLongT5-Large | [ViLongT5_large.gin]() | [storage-path]() |

## Finetunning

📄 Example with Flaxformer: [to-be-added]()


## Results

![image](https://user-images.githubusercontent.com/14871187/233701416-af11f6ff-40fd-4575-9727-fbb932cc76ed.png)


### Datasets
- [NewsCorpus](https://github.com/binhvq/news-corpus)
- [VMDS](https://github.com/lupanh/VietnameseMDS)
- [ViMS](https://github.com/CLC-HCMUS/ViMs-Dataset)

## Citation
```
@inproceedings{rusnachenko2023pretraining,
    title = "Pre-training {LongT5} for Vietnamese Mass-Media Multi-document Summarization Task",
    author = "Rusnachenko, Nicolay and Le, The Anh and Nguyen, Ngoc Diep",
    booktitle = "Proceedings of Artificial Intelligence and Natural Language",
    year = "2023"
}
```
