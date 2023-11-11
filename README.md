## LLM

### LLM with Llama 2 - RAG and  Fine Tuning 

#### Llama 2 with RAG

##### Requirements

- A colab jupyter notebook with T4 GPU

- Getting approval for using Llama 2

  - Step 1: Fill in the Llama 2 access request form

    Fill in the [Llama access request form](https://ai.meta.com/resources/models-and-libraries/llama-downloads/). You will need the Llama 2 & Llama Chat model but it            doesn’t hurt to get others in one go. You will have to use the email address associated with your HuggingFace account. Typically, you will receive the approval email         within an hour.

  - Step 2: Request access to the Llama 2 model

    Visit the [Llama 2 13B Chat model](https://huggingface.co/meta-llama/Llama-2-13b-chat-hf) page.You should see another request form for downloading the model.

- Using RAG with Llama 2

  There are three strings to be replaced in the notebook in order to run.

  - PINECONE\_API\_KEY: Pinecone API Key
  - PINECONE\_ENV: The environment associated with the API key
  - HF\_AUTH\_TOKEN: Hugging Face authorization token

  Pinecone API Key: Go to [Pinecone](https://app.pinecone.io/) and create a free account if you don’t have one. After signing in, click API Keys on the right panel. It        should show your API keys. You can use the default one or create a new one.
  
  Pinecone environment: Copy the Pinecone environment PINECONE\_ENV under the Environment header.
  
  Hugging Face authorization token: Go to the [Access token](https://huggingface.co/settings/tokens) page. Create a new one or use an old one.
  
##### Functionality

Large language models (LLM), such as Llama and GPT, are typically trained on broad datasets. They are not good at special domain knowledge. Instead of training a new model, using Retrieval-Augmented Generation (RAG) is a quick and cheap way to achieve a similar purpose.

-   Initializing the embedding pipeline that will handle the transformation of our docs into vector embeddings.
- Create document embedding using the embedding model.
-   Building the Vector Database: We will be using the pinecone vector index for our RAG pipeline. Using the embedding pipeline to build our embeddings and store them in a Pinecone vector index. Using the Pinecone API key to initialize the index.
- Used a set of Arxiv papers related to (and including) the Llama 2 research paper as the dataset to append our content store for the RAG pipeline.
- Integrate with langchain to connect the vector database
- Initialize the retrieval QA chain for the RAG pipeline, and add the vector database to the LLM for the RAG pipeline
- Compare LLM prompts with and without RAG 


#### Llama 2 Fine Tuning

##### Requirements

- A colab jupyter notebook with T4 GPU
- Access to the Hugging Face hub to push and pull models and data.

Functionality:

- Configure the llama-2-7b model to fit in T4 GPU and fine tune with guanaco-llama2-1k dataset.
- QLoRA was used to reduce the storage requirements, by storing the change in weights from fine tuning in two different smaller matrices.
- Create and load the model from Hugging Face.
- Trained the model with a new dataset and uploaded to the Hugging Face hub. 
