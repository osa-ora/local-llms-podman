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

6) You can use the local REST APIs for interaction with the ollama models as following:
```
ollama serve //if ollama is not working ...

//for normql one time output generation ..
curl http://localhost:11434/api/generate -d '{
  "model": "llama3.2",      
  "prompt":"Why is the sky blue?"
}'

//for chat conversation ..
curl http://localhost:11434/api/chat -d '{
  "model": "llama3.2",      
  "messages": [
    { "role": "user", "content": "why is the sky blue?" }
  ]                  
}'    

//configure the response requirements ..
curl -X POST http://localhost:11434/api/chat -H "Content-Type: application/json" -d '{
  "model": "llama3.2",
  "messages": [
    {
      "role": "user",
      "content": "Return a JSON array of the 10 famous writers in the world. Each object should include \"Name\" and \"Birth Date\". The response should be valid JSON without extra text."
    }
  ],
  "stream": false,
  "format": {
    "type": "array",
    "items": {
      "type": "object",
      "properties": {
        "Name": {
          "type": "string"
        },
        "Birth Date": {       
          "type": "string"
        }
      },
      "required": ["Name", "Birth Date"]      
    }
  }
}'

``` 

7) Let's now install a bette user experience chatbox, download ChatBox from here: https://chatboxai.app/en#download

8) Run the application and configure it to use the Ollama as following:

<img width="592" alt="Screenshot 2025-02-24 at 10 05 43 AM" src="https://github.com/user-attachments/assets/2231775e-3b7d-41ee-979f-9163b036d9b0" />

Go through the other tabs to configure any necessary information like font size, welcome message and may be network proxy or any other needed configuration.

Now try to chat with the application ..

<img width="1022" alt="Screenshot 2025-02-24 at 10 11 33 AM" src="https://github.com/user-attachments/assets/bc5fd6a7-d151-4ea5-85e9-4464cf2f9443" />

You may configure co-pilot as well.

<img width="1023" alt="Screenshot 2025-02-24 at 10 12 48 AM" src="https://github.com/user-attachments/assets/dfbd93d8-2e35-443b-bdbc-7910dc2139b1" />

You can pick any other client or community project from the full list on ollama: [https://github.com/ollama/ollama](https://github.com/ollama/ollama?tab=readme-ov-file#web--desktop)

Now you have a full local experience for using LLMs on your local laptop.

