# <p align="center"> 🚀**AI-Driven RAG Solution**🚀 </p> 

<p align="center"> **Elevating Customer Support with Multi-Platform Data** </p>


## 🌟**Instructions to Run the Code:**

1. **Open the final_rag.ipynb file** on Google Colab.
2. **Upload the CSV file** named `support_chat.csv` in this repository.
3. **Specify the local path** of the CSV file in the first cell.
4. **Run all the cells** to execute the code.
5. **Interact with the Gradio interface** by asking multiple queries. (Explanations for each part are embedded between the cells).


## 🛠️**Tech Stack & Tools:**

1. Langchain: For seamless language model integrations.
2. ChromaDB: Enhancing our database querying capabilities.
3. HuggingFace: Utilizing cutting-edge models for NLP.
4. Mistral-7b: Leveraging its powerful generative abilities.
5. Gradio: For an interactive and user-friendly interface.

## 👩‍💻**Project Insights**

1. **Data Indexing and Querying:**
   - **Vector Database:** Utilize **ChromaDB** from the Langchain community for efficient storage and querying of vector embeddings.
   - **Embedding Model:** Opted for the **HuggingFaceEmbeddings-all-mpnet-base-v2 model**, which is based on the Sentence Transformers base model. This model  allows you to generate embeddings for  				  sentences or text passages. Since our chats consist of multiple sentences separated by special tokens, using a sentence transformer-based model is suitable for preserving the 				  structure of our conversations.
   - **Data Storage:** Store the generated embeddings along with the associated metadata (such as chat IDs,annotations, etc.) in ChromaDB.
   - **Querying and Retrieval:** Retrieve embeddings from **ChromaDB** based on specific queries.
   - **Model and Tokenizer:** The code initializes a tokenizer using the pretrained model name **'mistralai/Mistral-7B-Instruct-v0.1'**. Mistral-7B-Instruct which prioritizes accuracy and 				context-awareness.Its use of rolling buffer caching efficiently retains relevant information across sequences
   - **Efficient Model Loading:** By utilizing **4-bit precision** base model loading (use_4bit=True), the code optimizes memory usage during model loading. it reduces the memory footprint and accelerates 					  loading times.
   - **Quantization for Reduced Precision:** The code implements quantization techniques such as **"nf4" (nearest float 4-bit)** to reduce the precision of model parameters and computations.This reduction 						     in precision helps conserve memory and computation resources.


2. **Query Preprocessing:**
   - Implement Prompt Template strategies to enhance query quality, including:
     a. **Removing Personal Information**
     b. **Answering Only Based on Available Data**
     c. **Restricting Sensitive information/Topics** (Marked topics as urgent for prioritization).


3. **Response Post-Processing:**
   - Use the **Langchain LLM chain architecture** for integrating components like retrievers, prompts, and language models. Note that the restricted topics and sensitive information have been tackled in 	Query preprocessing itself.


4. **Metadata Usage:**
   - Utilized metadata like **Topic**, **Topic Aspects**, and **Sentiments** for each unique conversation based on Ticket_id. Keywords such as 'subscription', 'refund', etc., are common in metadata, significantly enhancing retrieval query effectiveness.
