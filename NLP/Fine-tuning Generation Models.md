#LLM

There are two most common methods for fine-tuning text generation models, **supervised fine-tuning** and **preference tuning**.

## Supervised fine-tuning (SFT)
Goal: adapt the base LLM model to certain use-cases, e.g. following instructions.
![[Screenshot 2025-06-14 at 2.38.08 PM.png]]
### Full fine-tuning
In full fine-tuning, we will update all parameters of a model to be in line with the target tasks.

Difference between full fine-tuning and pre-training: pre-training is done on a large dataset but with no labels, while full fine-tuning is done on a smaller but labeled dataset.
![[Screenshot 2025-06-14 at 2.40.09 PM.png]]
### Parameter-efficient fine-tuning (PEFT)
Updating all parameters of a model is very costly, needs a long time to train, and requires significant storage. PEFT focus on fine-tuning pretrained models at higher computational efficiency.

**Adapters**
One way to achieve this is through **adapters**. Adapters are a set of additional modular components inside the transformer that can be fine-tuned to improve model's performance on a specific task without having to fine-tune all the model weights.
![[Screenshot 2025-06-14 at 2.44.28 PM.png]]

The collection of adapters spanning different part of the model can be viewed as a set, designed to be specialized in different tasks. For example, one set of adapters is specialized in text classification, another specialized in [[Name Entity Recognition]] etc. We can swap adapters specialize in specific tasks into the same architecture.

**Low-Rank Adaptation (LoRA)**
LoRA is another widely used and effective technique for PEFT. The idea is that we can decompose big LLM weight matrices into smaller matrices, which will greatly reduce the number of parameters to tune.
![[Screenshot 2025-06-14 at 2.48.36 PM.png]]
![[Screenshot 2025-06-14 at 2.49.35 PM.png]]

Research have found that language models "have a very low intrinsic dimension", indicating small ranks decomposition can lead to a very good approximate for the LLM weight matrices. In practice, one can choose the specific weight matrices to perform LoRA on (e.g. we can only fine-tune the query and value weight matrices in the transformer layer).

**QLoRA**
To increase efficiency even more, we can do model compression when using LoRA.

Quantization is basically mapping high precision float numbers to lower precision float numbers (e.g. float64 to float32). Specifically QLoRA uses a technique called blockwise quantization to reduce quantization error which can do 4-bit quantization.

## Preference tuning
SFT is mostly used to make the model do specific tasks (e.g. follow instructions), but we can further improve LLM's behavior by a final training phase that aligns it to how we expect it to behave in different scenarios, i.e. generate more preferable output.

### Gather human feedbacks
- Let the LLM produce pairs of outputs
- Let humans rate which output is better
### RLHF (Reinforcement learning with Human Feedback)

- Train a reward model to mimics human ratings
- LLM trains to receive high feedback from the reward model, but also constrained not to drift away too much from the original model (to avoid reward hacking.)
- The specific method is called PPO ([[Proximal Policy Optimization]])
- Disadvantage: Unstable, need to train a reward model which is large
### DPO (Direct Preference Optimization)
- Get rid of the reward model and reinforcement procedure, and formulate the problem as a contrastive learning setting.
- LLM assign high probability to positive example and low probability to negative examples, while not to drift away too much from the original model

## References
1. Hands on LLM, Chp. 12
2. [All about quantization](https://newsletter.maartengrootendorst.com/p/a-visual-guide-to-quantization)
3. [DPO](https://www.youtube.com/watch?v=XZLc09hkMwA)
4. https://www.youtube.com/watch?v=k2pD3k1485A
5. https://medium.com/@sinarya.114/d-p-o-vs-r-l-h-f-a-battle-for-fine-tuning-supremacy-in-language-models-04b273e7a173