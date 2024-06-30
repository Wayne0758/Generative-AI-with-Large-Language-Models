# Summarize Dialogue
This project we will use FLAN-T5 model to acknowledge the difference between no prompting engineering, 0 shot, 1 shot and few shot.
## Without Prompting
![image](https://github.com/Wayne0758/LLM/assets/120694819/f2a4ff2b-e271-48ef-9ae8-47a0173650a0)  
As you can see, the summarization didn't get the point.  
## 0 Shot  
![image](https://github.com/Wayne0758/LLM/assets/120694819/1e7b2aeb-7680-4d9a-aacb-82738e6067ea)  
The output hasn't improved. We move on to the next one.  
## 1 Shot  
![image](https://github.com/Wayne0758/LLM/assets/120694819/dcfd4b97-279f-4929-befc-a3ac52e7ba0c)  
The output is better than the previous one. So we now know that adding more shots may be helpful to the outcome.
## Few Shot  
![image](https://github.com/Wayne0758/LLM/assets/120694819/f3d0f271-f11c-4ab9-b695-950ae8746fe0)  
![image](https://github.com/Wayne0758/LLM/assets/120694819/5b56545a-c73b-45d1-8428-4e3e457a91f4)  
It seems weird that the output didn't change after adding more shots, but it is normal in many cases. Increasing the number of shots will not necessarily enhance the performance. So now we move on to the next technique.
## Generative configure parameters  
do_sample means we can adjust the parameters to activate different strategies which affect the probability distribution of the next token. Higher temperature means the randomness of token to make more creative content.
### GenerationConfig(max_new_tokens = 50)  
![image](https://github.com/Wayne0758/LLM/assets/120694819/5ba8c484-be69-49b0-a951-64cfb7ec1d82)  
### GenerationConfig(max_new_tokens = 10)  
![image](https://github.com/Wayne0758/LLM/assets/120694819/04d9e1e7-d58e-4072-a4c7-d78935cfaa5f)  
### GenerationConfig(max_new_tokens = 50, do_sample = True, temperature = 0.1)  
![image](https://github.com/Wayne0758/LLM/assets/120694819/868b7be0-8a91-4d82-899a-7a9ffe6699bd)  
### GenerationConfig(max_new_tokens = 50, do_sample = True, temperature = 0.5)  
![image](https://github.com/Wayne0758/LLM/assets/120694819/b018bbdc-81a2-4457-8185-a848a9e53c77)
### GenerationConfig(max_new_tokens = 50, do_sample = True, temperature = 1.0)  
![image](https://github.com/Wayne0758/LLM/assets/120694819/ec6dac56-3b6c-4ee8-9222-482d9de3e501)  
### GenerationConfig(max_new_tokens = 50, do_sample = True, temperature = 2.0)  
![image](https://github.com/Wayne0758/LLM/assets/120694819/42249ef4-c591-401a-8272-d91fbb6f8154)
