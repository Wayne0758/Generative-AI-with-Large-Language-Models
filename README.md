# LLM
This contains several projects from Generative-AI-with-Large-Language-Models in Coursera, including Summarization and Text generation, and so on.  
I made some changes to adapt to PC users since the original version is for AWS users.
# Note
There are some notes from Coursera and DeepLearning.AI down below. Hope it would be helpful for you.  

## Different models
### Autoencoding models
Known as encoder-only LLM.  
Using Masked Language Modeling (MLM).  
Objective: Predict next token ('denoising') by using Bidirectional context.  

#### Good applications:  
Sentiment analysis  
Named entity recognition  
Word classification  

#### For example:  
BERT  
ROBERTA  

### Autoregressive models
Known as decoder-only LLM.  
Using Causal Language Modeling (CLM).  
Objective: Reconstruct text by using Unidirectional context.  

#### Good applications:  
Text generation  
Other emergent behavior (Depends on model size)  

#### For example:  
GPT  
BLOOM  

### Seq2Seq models
Known as encoder-decoder LLM.  
Using Span Corruption.  
Objective: Reconstruct Span  

#### Good applications:  
Translation  
Text summarization  
Question answering  

#### For example:  
T5  
BART  

## Efficient Multi-GPU compute strategies
### Distributed Data Parallel (DDP)
We can use Distributed Data Parallel to improve the model's efficiency since sometimes the model is too big for a single GPU, dividing LLM into several GPUs and eventually Synchronizing gradients to update the model.  

### Fully Sharded Data Parallel (FSDP)
Reducing memory by distributing the model parameters, gradients and optimizer states across GPUs instead of replicating them.  

## Pre-training for domain adaptation
Different domains have their own special term. Using Pre-training for specific domain adaptation can be efficient and convenient.  

### BloombergGPT
BloombergGPT is a financial model, it is a good case of pre-training a model for increased domain-specificity.  

## Fine-tuning
Fine-tuning may cause Catastrophic Forgetting since if the model targets on specific goal, it may forget what it has learned before.  
Fine-tuning on Multi-task can avoid Catastrophic Forgetting.  
FLAN-T5 is a good example.  

## LLM evaluation metrics
$Accuracy = \frac{Correct Predictions}{Total Predictions}$

### ROUGE
Used for text summarization

#### ROUGE-1
$ROUGE-1-Recall  = \frac{unigram matches}{unigrams in reference}$  
$ROUGE-1-Precision  = \frac{unigram matches}{unigrams in output}$  
$ROUGE-1-F1  = {2}\times{\frac{{Precision}\times{Recall}}{Precision+Recall}}$   

#### ROUGE-2
$ROUGE-2-Recall  = \frac{bigram matches}{bigrams in reference}$  
$ROUGE-2-Precision  = \frac{bigram matches}{bigrams in output}$  
$ROUGE-2-F1  = {2}\times{\frac{{Precision}\times{Recall}}{Precision+Recall}}$  

#### ROUGE-L
Find the Longest common subsequence (LCS)  
$ROUGE-L-Recall  = \frac{LCS(Gen,Ref)}{unigrams in reference}$  
$ROUGE-L-Precision  = \frac{LCS(Gen,Ref)}{unigrams in output}$  
$ROUGE-L-F1  = {2}\times{\frac{{Precision}\times{Recall}}{Precision+Recall}}$  

### BLEU SCORE
Used for text translation  
$BLEU metric  = Avg(precision across range of n-gram sizes)$  

## Parameter efficient fine-tuning (PEFT)
Full fine-tuning is too taxing. PEFT can save space and be flexible.  

### PEFT methods
Selective: Select a subset of the initial LLM parameters to fine-tune.  
Reparameterization: Reparameterize model weight using a low-rank representation. (LoRA)  
Adaptive: add trainable layers or parameters to the model  

### Low-rank Adaption to LLM (LoRA)
1. Freeze most of the original LLM weights.  
2. inject 2 rank decomposition matrices.  
3. Train the weights of the smaller matrices.  
Steps to update the model for inference:  
1. Matrix multiply the low-rank matrices.  
${B}\times{A}$  
2. Add to original weights.  
$Freezed weights + {B}\times{A}$  
By doing this, we can efficiently reduce the parameters that we adjust, so it can perform on a single GPU.

### Soft Prompt 
Prompt tuning is not Prompt engineering.  
Prompt tuning means adding additional tokens in inputs. Those tokens are called Soft Prompts.  
Prompt tuning can be as successful as Full fine-tuning.  

## Reinforcement Learning from Human Feedback (RLHF)
Models' behaving badly:  
Toxic language  
Aggressive responses  
Providing dangerous information  

HHH is a standard to evaluate the model's behavior.  
HHH:  
Helpful  
Honest  
Harmless  

### RLHF in text summarization
Fine-tuning with human feedback is better than initial fine-tuning, no fine-tuning, and even the reference human baseline.  
RLHF can maximize helpfulness and relevance, minimize harm, and bypass dangerous topics.  

### Reinforcement Learning
The agent will get feedback from the environment.  
The goal is to get the maximum cumulative reward from the environment.  

### Reinforcement Learning: fine-tuned LLMs
If LLMs achieve HHH standards, then the reward is higher than if they don't.  

### Human feedback collection
Define the model alignment criteria like helpfulness, honestness, or harmlessness.  
Prompt -> LLM -> several completions  
Label the completions by the standard.  
The score may be divided from person to person, so we have to collect multiple responses from different people.  

### Reward model
Use the reward model as a binary classifier (positive or negative).  

### Fine-tuning with Reinforcement Learning
Prompt Dataset -> RL-updated LLM -> Reward Model -> RL algorithm -> (go back to RL-updated LLM) (iterate until it aligns human responses)

### Proximal Policy Optimization (PPO) 
PPO is an RL algorithm.  
The goal is to update the policy so that the reward is maximized.  
#### PPO Phase 1
The reward model will value the completion.  
PPO is to minimize value loss to tell LLM whether this time is a good training.  

#### PPO Phase 2  
Calculate policy loss:  
Maximizing this expression results in a better human-aligned LLM.  
Calculate entropy loss:  
Entropy makes the model remain creative.  
Higher entropy leads to higher creativity.  
Objective function:  
$L^{PPO} = L^{POLICY} + c1L^{VF} + c2L^{ENT}$  
  
After many iterations, the human-aligned model will come out.  

### RLHF: Reward hacking  
If we use a very harmful model to evaluate the result, we may have trained a very bad model.  
How to avoid Reward hacking:  
KL Divergence Shift Penalty  
This will compare RL-updated LLM with the Reference Model.  
KL Divergence Shift Penalty gets added to the reward and put into PPO with the reward.  
How to evaluate the human-aligned LLM:  
Give a test dataset.  
Make the Instruct LLM and the Human-aligned LLM generate the output.  
Feed the reward model with their outputs.  
Compare their score to evaluate whether the human-aligned LLM is better than the Instruct LLM.  











