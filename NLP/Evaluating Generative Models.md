## Word-level metrics
Comparing a reference dataset with the generated tokens on a token(set) level. Common word-level metrics include [[Perplexity]], ROUGE, BLEU, and BERTScore.

## Benchmarks
Another common method is to use benchmarks such as MMLU, GLUE, TruthfulQA, GSM8k, and HellaSwag. There are leaderboards that one can use when selecting the model to use.

One disadvantage is that models can be overfitted to these public benchmarks.

## Automated Evaluation
A separate LLM can be used to do evaluation as well, namely the LLM-as-a-judge method. One can also do pairwise comparison like two different LLMs generate an answer to a question and a third LLM will be the judge to declare which is better.

Advantage is that this allow for automated evaluation of open-ended questions.

## Human Evaluation
Human evaluation is still not replaceable for LLM evaluation. One platform is [Chatbot Arena](https://lmarena.ai) which asks the community to vote the output they prefer of different LLMs.