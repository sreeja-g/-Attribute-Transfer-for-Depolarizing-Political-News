# Description

This is an implementation of the DeleteOnly and DeleteAndRetrieve models from [Delete, Retrieve, Generate:
A Simple Approach to Sentiment and Style Transfer](https://arxiv.org/pdf/1804.06437.pdf) (implemention: https://github.com/rpryzant/delete_retrieve_generate/tree/master)

# Installation

`pip3 install -r requirements.txt` 

# Usage

### Training 

`python3 train.py --config polarity_config.json --bleu`

`model_type`: `delete`, `delete_retrieve`, or `seq2seq` (which is a standard translation-style model).

### Inference

`python inference.py --config polarity_config.json --checkpoint path/to/model.ckpt`

To run inference, you can point the `src_test` and `tgt_test` fields in your config to new data. 


### Data prep

Given two pre-tokenized corpus files, use the scripts in `tools/` to generate a vocabulary and attribute vocabulary:

```
python tools/make_vocab.py [entire corpus file (src + tgt cat'd)] [vocab size] > vocab.txt
python tools/make_attribute_vocab.py vocab.txt [corpus src file] [corpus tgt file] [salience ratio] > attribute_vocab.txt
python tools/make_ngram_attribute_vocab.py vocab.txt [corpus src file] [corpus tgt file] [salience ratio] > attribute_vocab.txt
```

# Citation

If you use this code as part of your own research can you please cite 

(1) the original paper:
```
@inproceedings{li2018transfer,
 author = {Juncen Li and Robin Jia and He He and Percy Liang},
 booktitle = {North American Association for Computational Linguistics (NAACL)},
 title = {Delete, Retrieve, Generate: A Simple Approach to Sentiment and Style Transfer},
 url = {https://nlp.stanford.edu/pubs/li2018transfer.pdf},
 year = {2018}
}

```

(2) The paper that this implementation was developed for:
```
@inproceedings{pryzant2020bias,
 author = {Pryzant, Reid and Richard, Diehl Martinez and Dass, Nathan and Kurohashi, Sadao and Jurafsky, Dan and Yang, Diyi},
 booktitle = {Association for the Advancement of Artificial Intelligence (AAAI)},
 link = {https://nlp.stanford.edu/pubs/pryzant2020bias.pdf},
 title = {Automatically Neutralizing Subjective Bias in Text},
 url = {https://nlp.stanford.edu/pubs/pryzant2020bias.pdf},
 year = {2020}
}
```

