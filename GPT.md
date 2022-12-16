## High Level Summary
Generative Pretrained Transformer is a pretrained decoder part of a [[Transformer]].

## Detail
- Transformer decoder with 12 layers
- 768 dimensional hidden states, 3072 dimensional feed-forward hidden layers
- [[Byte Pair Encoding (BPE)]]
- Trained on BooksCorpus

## Pretraining decoders
It is natural to pretrain decoders as language models, and then use them as generators

## Finetuning
Format inputs to the decoder for finetuning tasks
