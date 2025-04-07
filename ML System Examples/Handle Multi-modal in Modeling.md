There are two commonly used fusing methods to combine heterogeneous data: late fusion and early fusion.We use [[04. Harmful Content Detection]] as an example

## Late fusion
In late fusion, ML models process different modalities independently, then combine their predictions to make a final decision.
![[Pasted image 20250407151625.png]]
**Advantages**
- We can train, evaluate and improve each model independently
**Disadvantages**
- Training is time-consuming and expensive
- The combination of the modalities might be harmful, even if each is benign in isolation. In this case, late fusion fails.
## Early fusion
In early fusion, modalities are combined first (usually by concatenating their feature vectors), then we have a single model to make a prediction.
![[Pasted image 20250407151723.png]]
**Advantages**
- Training is cheaper because we only need to train one model
- Can handle the problem that each component is benign, but combination is harmful
- Don't need to collect data separately for each modality.
**Disadvantages**
- More difficult to learn, especially when there is not enough training data.