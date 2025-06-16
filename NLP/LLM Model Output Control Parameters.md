#LLM 

### Temperature
The `temperature` controls the randomness or creativity of the text generated. It defines how likely it is to choose tokens that are less probable. The underlying idea is that a temperature of 0 generates the same response every time because it always chooses the most likely word. As illustrated in the below figure, a higher value allows less probable words to be generated.
![[Screenshot 2025-06-15 at 7.55.47 PM.png]]
**One line summary: 
higher temperature -> more diverse output
lower temperature -> more deterministic output**

### top_p
`top_p`, also known as nucleus sampling, is a sampling technique that controls which subset of tokens (the nucleus) the LLM can consider. It will consider tokens until it reaches their cumulative probability.

One line summary: lower `top_p` -> consider less tokens, less creative; higher `top_p` -> more creative (1 is the maximum number)

### top_k
`top_k` parameter controls exactly how many tokens the LLM can consider. If you change its value to 100, the LLM will only consider the top 100 most probable tokens.

### Choosing parameters
Selecting the parameters values depends on use-cases, for example:
- Brainstorming session: high `temperature`, high `top_p`, so we will have maximum creativity
- Email generation: low `temperature`, low `top_p`, since we want more predictable, focused and conservative outputs
- Creative writing: high `temperature`, low `top_p`, high randomness with a small pool of potential tokens. This combination produces creative outputs but still remains coherent
- Translation: low `temperature`, high `top_p`, deterministic output with high probable predicted tokens. Produces coherent output with a wider range of vocabulary, leading to outputs with linguistic variety.
