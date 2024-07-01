# Project 2
This project is targetting the difference between without fine-tuning, fully fine-tuning, and PEFT.  
I made some changes to let it fit my PC limitation.
## LAB
Since my GPU does not have enough space, I lowered the batch size from 8 to 4.  
![image](https://github.com/Wayne0758/LLM/assets/120694819/bc0a32b3-b2ed-4769-8566-edecb1719063)  
  
I download the fully fine-tuning model from the library instead of AWS.  
![image](https://github.com/Wayne0758/LLM/assets/120694819/236b728a-97e7-4f3b-886d-e523065a5d2a)  
  
![image](https://github.com/Wayne0758/LLM/assets/120694819/ca0ee161-0f99-47d9-a34b-42c35d39c831)  
  
Comparison  
'./dialogue-summary-training-results.csv' is to evaluate on a larger section of data  
![image](https://github.com/Wayne0758/LLM/assets/120694819/1aac94ec-de85-4221-a9aa-38723934c67a)  
  
Scores improvement in all ROUGE metrics  
![image](https://github.com/Wayne0758/LLM/assets/120694819/c44d3e9c-a9ad-46cd-b699-21fca6ced7fe)  
  
Setup the PEFT/LoRA model for Fine-Tuning  
![image](https://github.com/Wayne0758/LLM/assets/120694819/20b29abd-14a1-4785-9fe5-f2711e0cc97d)  
  
Train PEFT Adapter  
![image](https://github.com/Wayne0758/LLM/assets/120694819/8f8152d9-67e0-4464-aaf9-af47e1b06fe3)  
  
I download the PEFT model from the library instead of AWS  
![image](https://github.com/Wayne0758/LLM/assets/120694819/c781e741-68e3-4e6f-85b0-8bf65363fac6)  
  
![image](https://github.com/Wayne0758/LLM/assets/120694819/ceb4bab7-85fe-46a5-ac3b-f07eb9fa9a46)  
  
Comparison  
![image](https://github.com/Wayne0758/LLM/assets/120694819/02b068bc-9caa-4c76-9c33-02a89d90048e)  
'./dialogue-summary-training-results.csv' is to evaluate on a larger section of data  
![image](https://github.com/Wayne0758/LLM/assets/120694819/0fa683d7-eb28-4f1f-bf94-8bd5d864a5fe)  
  
Scores improvement in all ROUGE metrics  
![image](https://github.com/Wayne0758/LLM/assets/120694819/b0a4d1b6-f36c-4395-87a1-c5a1fa991c61)  
