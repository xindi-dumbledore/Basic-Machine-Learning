#multimodal #LLM 

How can we extend pre-trained LLM to have vision capacity?

BLIP-2 bridges the visionlanguage gap by building a bridge, named the Querying Transformer (QFormer), that connects a pretrained image encoder and a pretrained LLM. By leveraging pretrained models, BLIP-2 only needs to train the bridge without needing to train the image encoder and LLM from scratch.
![[Screenshot 2025-06-16 at 8.54.37 AM.png]]
To connect the two pretrained models, the Q-Former mimics their architectures. It has two modules that share their attention layers:
- An Image Transformer to interact with the frozen Vision Transformer for feature extraction
- A Text Transformer that can interact with the LLM

## Training BLIP-2
Step 1:
Representation learning is applied to learn representations for vision and language simultaneously. 
![[Screenshot 2025-06-16 at 8.57.17 AM.png]]
Step 2, these representations are converted to soft visual prompts to feed the LLM.
![[Screenshot 2025-06-16 at 8.57.33 AM.png]]