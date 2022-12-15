## One Line Summary
Seq2Seq is a neural network architecture which take a sequence as input and generate a sequence as output. It involves two [[Recurrent Neural Networks (RNN)]], and is also called encoder-decoder architecture.

![[seq2seq.png]]
## Detail
- The seq2seq model is an example of a conditional language model
	- LM because the decoder is predicting the next word of the target sentence $y$ given target words so far
	- Conditional because its predictions are also conditioned on the source sentence $x$
- Taking neural machine translation as an example, seq2seq estimates $$P(y|x) = P(y_1|x)P(y_2|y_1,x)...P(y_T|y_1, ..., y_{T-1},x)$$
### Training
End-to-End, the cost function is calculated on the target sequence.
![[seq2seq_train.png]]
### Test time decoding
- Greedy decoding
	- At each time step, take the most probable word
	- Problem: it's greedy, it can't undo decisions
- Exhaustive search decoding
	- Compute all possible sequence $y$ and pick the highest one
	- Problem: too expensive!
- Beam search encoding
	- At each step of the decoder, keep track of the $k$ most probable partial translations (hypotheses)
	- Stopping criteria
		- We reach timestep $T$
		- We have at least $n$ completed hypotheses (i.e. produce `<END>`)
	- At the end we pick the hypotheses with highest scoring (formalized by length) $$\frac{1}{t}\log P_{LM}(y_i|y_1, ..., y_{i-1}, x)$$