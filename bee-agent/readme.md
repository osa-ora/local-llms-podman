# Deploy Bee Agent on your machine using Podman Compose
---

In this tutorial we will deploy the Bee Agent and configure it to run with Deep Seek model in our local laptop.

Bee Agent Framework: As described in its GitHub: https://github.com/i-am-bee/bee-agent-framework
It is an Open-source framework for building, deploying, and serving powerful multi-agent workflows at scale.
🐝 Bee Agent Framework is an open-source TypeScript library for building production-ready multi-agent systems. Pick from a variety of 🌐 LLM providers, customize the 📜 prompt templates, create 🤖 agents, equip agents with pre-made 🛠️ tools, and orchestrate 🤖🤝🤖 multi-agent workflows! 🪄

---
Pre-requists: 
Podman for Desktop, Ollama installed on your machine with enough memory, CPU and storage.

You can download Podman for Desktop from this location: (🔗 https://podman-desktop.io/) 
We Will use Podman compose to deploy the agent: (🔗 https://podman-desktop.io/docs/compose/setting-up-compose)

Download Ollama and install it: 🔗 https://ollama.com/download

Once install you can download any models you want to use using: 
```
   ollama pull llama3.1 //the current default at the writing of this post
   ollama pull llama3.2
   ollama pull deepseek-r1:8b
   ollama pull granite3.1-dense:8b
   ollama list //to view the downloaded models
   ollama rm granite3.1-dense:8b // to delete any model, just rm the model_name
```

You can chat to any of these models using the following command. (Note: Control+D to stop and exit the interactive mode).
```
  ollama run llama3.2
```
Now make sure Podman desktop is running, and as Bee Stack needs the container runtime to run as root. You can check if Rootless is false (which means Podman is running as root).
```
  podman machine start 
  podman compose -v //check podman compose is available
  podman info //check if Host --> Security --> Rootless equal to false)
```
if rootless is ture, you can configure it using: 
```
  podman machine stop
  podman machine set - rootful=false
  podman machine start
```

Run the Bee Stack with the default llama3.1
```
  git clone https://github.com/i-am-bee/bee-stack.git
  cd bee-stack
  ./bee-stack.sh setup  //select provider as ollama and when asked for the OLLAMA_URL hit enter and accept the default http://host.docker.internal:11434
```
You can now control the bess-stack using the following commands:

```
  ./bee-stack.sh setup 
  ./bee-stack.sh start
  ./bee-stack.sh stop
  ./bee-stack.sh clean
``` 
Start the stack (using start parameter) and access the given endpoint at 🔗 http://localhost:3000

<img width="886" alt="Screenshot 2025-02-08 at 2 59 18 PM" src="https://github.com/user-attachments/assets/54437c4d-fe78-480e-82e6-4469fe50ab49" />

Now you can use the GUI of this stack:

<img width="1461" alt="Screenshot 2025-02-08 at 3 01 01 PM" src="https://github.com/user-attachments/assets/b8ab07ed-d524-4a4e-ac5f-e8e70c5efe96" />

<img width="1468" alt="Screenshot 2025-02-08 at 3 09 27 PM" src="https://github.com/user-attachments/assets/cf973a99-ab82-43e5-ab0d-b4256cbb7d46" />

<img width="1032" alt="Screenshot 2025-02-08 at 3 10 32 PM" src="https://github.com/user-attachments/assets/037ec25b-cdf6-4f86-994e-5d9b32b45211" />

You can also access the APIs documentations using: 🔗 http://localhost:4000/docs/static/index.html

<img width="1448" alt="Screenshot 2025-02-08 at 3 06 08 PM" src="https://github.com/user-attachments/assets/98221efc-8472-40bc-965a-915183d030a9" />

If we execute the get API call of assistance, we can see the existing assistance and their model mapping:

```
curl -X 'GET' 'http://localhost:4000/v1/assistants?limit=20&order=desc&order_by=created_at&public=false' \
  -H "Authorization: Bearer ${BEE_API_KEY:-sk-proj-testkey}" \
  -H 'accept: application/json'
{"data":[
{"id":"asst_67a73955f96e809aba9d5857","object":"assistant","tools":[],"tool_resources":null,"instructions":null,"name":"Builder Assistant","description":"An example streamlit agent, tailored for building Streamlit applications.","metadata":{"$ui_color":"white","$ui_icon":"Bee"},"created_at":1739012437,"model":"llama3.1","agent":"streamlit"}
,{"id":"asst_67a73955f96e809aba9d5856","object":"assistant","tools":[{"type":"system","system":{"id":"web_search"}},{"type":"system","system":{"id":"weather"}},{"type":"system","system":{"id":"wikipedia"}},{"type":"code_interpreter"}],"tool_resources":null,"instructions":null,"name":"Bee Assistant","description":"An example agent powered by ReAct, not tailored to any specific task","metadata":{"$ui_color":"black","$ui_icon":"Bee"},"created_at":1739012437,"model":"llama3.1","agent":"bee"}],"first_id":"asst_67a73955f96e809aba9d5857","last_id":"asst_67a73955f96e809aba9d5856","has_more":false,"total_count":2}%                   
```
You can see the default value of "model":"llama3.1" in the response of these assistance.

To switch to another LLM for example Deep Seek, you can just pull the model using ollama as we did before then configure the assistance or any other component to use this model using a Post API call:
```
  curl -X POST \
  "${BEE_API:-localhost:4000}/v1/assistants" \
  -H "Authorization: Bearer ${BEE_API_KEY:-sk-proj-testkey}" \
  -H "Content-Type: application/json" \
  -d '{
  "name": "DeepSeek assistant",
  "model": "deepseek-r1:8b"
  }'
``` 
Note that we specified the assistant name and the exact name of the model in ollama list response to use: "name": "DeepSeek assistant","model": "deepseek-r1:8b"

You can confirm that by calling the get API again to see the new assistance details with the new model name.

If you switch back to the GUI you can see the new assistance named "DeepSeek assistant" is available and we can start chatting with it.

<img width="1444" alt="Screenshot 2025-02-08 at 3 36 09 PM" src="https://github.com/user-attachments/assets/34564fe8-8279-411f-860e-9161214fad81" />


Reference:
For more details see: 🔗 https://medium.com/hybrid-cloud-engineering/getting-started-with-a-local-setup-of-the-bee-agent-platform-6197db308e19







