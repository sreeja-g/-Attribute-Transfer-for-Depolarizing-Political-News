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


