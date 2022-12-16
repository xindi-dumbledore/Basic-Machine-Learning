#NLP #pretrain
### High level summary
Bidirectional Encoder Representations from Transformers (BERT) is a pretrained encoder part of a [[Transformer]].

## BERT Pretraining
Bert is pretrained on two tasks (combined?): Masked LM and Next sentence prediction.

### Masked LM
Encoders get bidirectional context, so we can't use language modeling as training objective.

Replace some fraction of words in the input with a special `[MASK]` token. Train the encoders to predict these words. This is also called Masked LM.

In BERT, to make it more robust, the masking process is as follows:
- Select a random 15% of (sub)word tokens
- Replace input word with `[MASK]` 80% of the time
- Replace input word with a random token 10% of the time
- Leave input word unchanged 10% of the time (but still predict it!) -> because in finetuning, we don't have `[MASK]` tokens

### Next sentence prediction
Generate a dataset of pairs of sentences (A, B). 50% of the time B is the actual next sentence follows A and 50% B is a random sentence.

## BERT input format
`[CLS] sentence 1 [SEP] sentence 2 [SEP]`