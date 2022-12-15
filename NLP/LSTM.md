## One Line Summary
LSTM (Long Short-Term Memory RNNs) is a type of [[Recurrent Neural Networks (RNN)]] as a solution to the vanishing gradients problem.

## Detail
### General idea
- At each time step $t$, here is a hidden state $h^{(t)}$ and a cell state $c^{(t)}$, both are vectors length $n$
- The cell stores long-term information
- The LSTM can read, erase and write information from the cell
- The selection of which information is erases/written/read is controlled by three corresponding gates
	- Forget gate: controls what is kept vs forgotten, from previous cell state
	- Input gate: controls what parts of the new cell content are written to cell
	- Output gate: controls what parts of cell are output to hidden state
- Apply the gates
	- At each time step, we first calculate some new cell content based on previous hidden states and current input
	- New cell state is a sum of last cell state through forget gate, and new cell content through input gate
	- New hidden state is the new cell state through output gate
![[lstm_eq.png]]