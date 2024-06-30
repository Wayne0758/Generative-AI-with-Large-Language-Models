# LLM
This contains several projects about LLM topics, including Summarization and Text generation, and so on. 
# Note
There are some notes from Coursera down below. Hope it would be helpful for you.  
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
