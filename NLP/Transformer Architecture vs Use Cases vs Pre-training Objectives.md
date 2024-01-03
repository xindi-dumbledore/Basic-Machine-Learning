#LLM #LLMPretraining
### Encoder-only LLM
- also called auto-encoding models
- **Pre-training Objective** trained with Masked Language Modeling (MLM): mask some of the tokens and use surrounding context tokens to predict them
- **good use cases**
	- sentiment analysis
	- named entity recognition
	- word classification
- **model example**
	- BERT
	- ROBERTA
### Decoder-only LLM
- also called autoregressive models
- **Pre-training Objective** trained with Causal Language Modeling (CLM): predict next tokens given previous tokens
- **good use cases**
	- text generation
- **model example**
	- GPT
	- Bloom
### Encoder-Decoder LLM
- original transformer architecture, seq-to-seq model
- **Pre-training Objective** training objectives can vary, T5 uses span corruption: mask random tokens and replace them with a sentinel token, the goal is to predict this sentinel token (which can be multiple tokens)
- **good use cases**
	- translation
	- text summarization
	- question answering
- **model example**
	- T5
	- BART

![[LLM_pretraining_objectives.png]]