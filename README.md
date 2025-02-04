# Deploy Local LLMs using Podman Desktop AI Lab

Guide on how to Deploy Local LLM Models 

Podman for Desktop has an AI Lab plugins that let's you deploy some models from the predefine model catalgs.

<img width="1494" alt="Screenshot 2025-02-04 at 11 47 38 AM" src="https://github.com/user-attachments/assets/d84a76bf-4363-42f1-8f4f-795dbbb54579" />

In case the model is not there, you can simply download it, import it and deploy it.

Let's take an example DeepSeek model.

### 1) Find and Download the Model: let's first find optimized i.e. quantized model in HuggingFace (.gguf) , for example: https://huggingface.co/unsloth/DeepSeek-R1-Distill-Llama-8B-GGUF

<img width="941" alt="Screenshot 2025-02-04 at 11 50 48 AM" src="https://github.com/user-attachments/assets/72aec2b1-eca0-4131-93cd-e4eb1db99d2d" />

Go to "Files & Versions" sections, and click on one of these models:

<img width="931" alt="Screenshot 2025-02-04 at 11 51 38 AM" src="https://github.com/user-attachments/assets/b0fbd114-cbea-4565-97da-55cc5a976614" />

Now click on the download icon to download this model.

### 2) Import the Model:
From Podman ==> Models ==> Catalog , then go to imprt model and select the model you just downloaded (gguf file) and the model will be imported in Podman AI catalog.

<img width="1206" alt="Screenshot 2025-02-04 at 11 59 11 AM" src="https://github.com/user-attachments/assets/12fef04e-8daa-4a5a-bf7d-e5fbd4a42b5e" />

Now, the model will be available in the catalog for deployment.

<img width="1211" alt="Screenshot 2025-02-04 at 11 59 50 AM" src="https://github.com/user-attachments/assets/f7893e9c-99d8-4054-a5aa-1491954533b0" />

### 3) Deploy the Model:
Create a service for that model:

<img width="1213" alt="Screenshot 2025-02-04 at 12 00 52 PM" src="https://github.com/user-attachments/assets/ab55bc03-12d3-4ba0-aabd-3794d9ddfda3" />

Once it is deployed, go to playground and create a new playground using that model service:

<img width="1194" alt="Screenshot 2025-02-04 at 12 02 40 PM" src="https://github.com/user-attachments/assets/d88f5687-d6cc-44c0-8b49-b0701e5c930b" />

### 4) Test/Chat with the Model:
Use the playground to chat with the model:

<img width="1212" alt="Screenshot 2025-02-04 at 12 03 19 PM" src="https://github.com/user-attachments/assets/c7194aff-d24b-4f93-9e42-2ec72ca6f851" />




