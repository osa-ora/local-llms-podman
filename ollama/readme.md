# Deploy LLMs on your machine using Ollama
---

In this tutorial we will deploy the LLMs using Ollama in particular the Deep Seek model in our local laptop.

1) Download Ollama and install it: 🔗 https://ollama.com/download

<img width="472" alt="Screenshot 2025-02-09 at 11 33 49 AM" src="https://github.com/user-attachments/assets/399ebaf2-ff52-4aad-8619-de4371ccd370" />

2) Search for the Model that you need to use:
 
<img width="1484" alt="Screenshot 2025-02-09 at 11 31 27 AM" src="https://github.com/user-attachments/assets/9809ae2e-9761-4609-80b7-6052eb0587a0" />

3) Select the best model that fits your machine specifications
   
You should have at least 8 GB of RAM available to run the 7B models, 16 GB to run the 13B models, and 32 GB to run the 33B models.

<img width="792" alt="Screenshot 2025-02-09 at 11 33 16 AM" src="https://github.com/user-attachments/assets/4cd0d64e-75a6-4d61-9491-a17d460f2232" />

4) Download the models you want to use using the ollama pull command.
```
   ollama pull llama3.2
   ollama pull deepseek-r1:8b
   ollama list //to view the downloaded models
   ollama rm llama3.2 // to delete any downloaded model, just rm the model_name
```

5) You can chat to any of these models using the ollama run command. 

```
  ollama run deepseek-r1:8b
```

<img width="867" alt="Screenshot 2025-02-09 at 11 29 43 AM" src="https://github.com/user-attachments/assets/14034af8-2228-4523-94a8-236155578ad6" />

Note: Control+D to stop and exit the interactive chat.
