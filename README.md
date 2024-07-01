# LLM
This contains several projects about LLM topics, including Summarization and Text generation, and so on.  
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











