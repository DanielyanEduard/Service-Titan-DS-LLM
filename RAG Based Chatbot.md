## <a name="_1y0mjq6yl0"></a>**Objective of the Project**
## <a name="_ugciz2hc9gwo"></a>Design and implement a Retrieval-Augmented Generation (RAG) chatbot to assist users in understanding and using PDF installation manuals for various home equipment.
1. ## <a name="_5bs526soebwp"></a>**PDF Processor**

For PDF text extraction in Python, I would choose PyMuPdf for its high cosine and tf-idf similarity and fast processing time. I am not entirely familiar with this technique and retrieved this information from

[*https://medium.com/social-impact-analytics/comparing-4-methods-for-pdf-text-extraction-in-python-fd34531034f](https://medium.com/social-impact-analytics/comparing-4-methods-for-pdf-text-extraction-in-python-fd34531034f)*.* 

Challenge 1. **Extracting text from tables.**

*Solution:* Use NLP techniques to clean and format the extracted data from tables.

Challenge 2. **Recognize text from diagrams or other structured formats.**

*Solution:* Use image recognition techniques to extract text from images and diagrams. Use OCR (Optical Character Recognition) tools like Tesseract. Tesseract can recognize the text embedded in images.


**2․ Embedding**

I have already used BERT to embed text. BERT allows us to understand the relationships between words and phrases in a given context. BERT can be fine-tuned for specific tasks, making it adaptable to various applications, from sentiment analysis to named entity recognition.  However, OpenAI can handle large datasets with a massive number of parameters. So, the choice of embedder depends on more features of the task and data.

Challenge 1. **There will be specific words in each manual.**

*Solution:* Fine-Tuning: Fine-tune pre-trained models on a corpus of installation manuals and “bert-base-uncased” (BERT case) to improve their understanding of specific vocabulary.

Challenge 2. **High dimensionality of embedding vectors.**

*Solution:* Use dimensionality reduction techniques. I am familiar with PCA, which worked well on all the data I used. 

**3. Vector Database**

I would use Pinecon because Pinecone offers blazing-fast search capabilities, allowing users to retrieve similar vectors in real-time and making it well-suited for applications like recommendation engines and content-based searching. I have not used this technique yet but retrieved this information from <https://medium.com/@woyera/pinecone-vs-chroma-the-pros-and-cons-2b0b7628f48f>.

Challenge 1. **Because of big data, there can be query latency.**

*Solution*: Store frequently accessed data in memory rather than on disk and implement parallel processing techniques.

Challenge 2. **Manuals contain images, diagrams, etc., which must be embedded and queried.**

*Solution*: I would store image and text embeddings in Pinecone, and I would use OpenAI CLIP for embedding.


#### <a name="_vwotq9p8num2"></a>**4. LLM Response Generation**
#### <a name="_vqty3pxep2hy"></a>I would use OpenAI GPT-4 for LLM Response Generation because it works better than BERT on generating tasks.

Challenge 1. **The response can be inaccurate.**

*Solution*: Use a fine-tuned model to improve response accuracy.

Challenge 2. **Users can respond in another language. For example, manuals are in English, and user responses are in Armenian.**

*Solution*: Translate the response to the language of manuals with the NLP model. I would use transformers for translation.





- 5 examples of complex questions that the chatbot will be able to answer.

1\. What are the steps to install an air conditioner?

**Response**: The chatbot can retrieve the installation steps written in the manual.

**Reason**: installation steps are written in manuals.

2\. How can I reset my wifi router?

**Response**: The chatbot can retrieve the steps for resetting as written in the manual.

**Reason**: Resetting steps are written in manuals.

3\. How can I contact the office that created my washing machine?

**Response**: Mail, address, or phone number of the office.

**Reason**: Contact information is usually at the end of the manuals.

4\. Can I get an installation with images?

**Response**: Images of installation with steps.

**Reason**: There is usually installation with images in manuals.

4\. How can I connect my coffee machine to my smartphone?

**Response**: Connection guide.

**Reason**: There is a guide of connection in manuals.

The model can answer the questions that are answered in manuals.

- 5 examples of questions that chatbot will fail to answer.

1\. Can you compare the model1 with the model2?

**Reason**: To compare, we need a comparative analysis model.

2\.  How to install a “model” wifi router?

**Reason**: If there is no manual about “model,” the model can’t answer.

3\. Why is my fridge not working?

**Reason**: To answer this question, it needs to diagnose the fridge.

4\. How can I buy more “model” products?

**Reason**: We have information only in manuals, and in manuals, there can be no information about buying.

5\. How much electricity will I use to heat my home with the air conditioner?

**Reason**: To answer this question, we need information about the home and a model that can calculate the cost.

The model can't answer the questions that are not answered in manuals.



