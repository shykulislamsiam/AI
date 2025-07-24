Bengali-English RAG Question Answering System

This project implements a Retrieval-Augmented Generation (RAG) system that answers questions in Bengali and English based on the "HSC26 Bangla 1st Paper" textbook PDF. It uses open-source tools and models without requiring API keys.

Setup Guide
-----------

1. Clone or download this repository.

2. Install dependencies using:
   pip install -r requirements.txt

3. Place the PDF file "HSC26_Bangla_1st_Paper.pdf" in the project root directory.

4. Run the main script:
   python main.py

Tools, Libraries, and Packages Used
-----------------------------------

- langchain: Document loading, chunking, and retrieval chaining
- chromadb: Local vector database for efficient similarity search
- sentence-transformers: Embedding model for semantic text representation
- transformers: HuggingFace pipeline for question answering
- pypdf: Extract text from PDF documents
- torch: Required by transformers

Sample Queries and Outputs
--------------------------

Bengali Queries:
- অনুপমের ভাষায় সুপুরুষ কাকে বলা হয়েছে? --> শুম্ভুনাথ
- কাকে অনুপমের ভাগ্য দেবতা বলে উল্লেখ করা হয়েছে? --> মামাকে
- বিয়ের সময় কল্যাণীর প্রকৃত বয়স কত ছিল? --> ১৫ বছর

English Queries:
- Who is described as a handsome man by Anupom? --> Shumbhonath
- Who is referred to as the god of fate by Anupom? --> His maternal uncle

Design Decisions and Technical Details
--------------------------------------

1. Text Extraction:
   Used PyPDFLoader from LangChain for page-wise PDF text extraction. Minor formatting issues (line breaks, headers) were handled via cleaning.

2. Chunking Strategy:
   RecursiveCharacterTextSplitter with 500 character chunks and 50 character overlaps. This balances context size and semantic retrieval accuracy.

3. Embedding Model:
   sentence-transformers/paraphrase-multilingual-MiniLM-L12-v2 was used for multilingual Bengali-English embeddings capturing semantic meaning effectively.

4. Query-Chunk Comparison:
   Cosine similarity on embeddings stored in Chroma vector database ensures efficient and meaningful similarity search.

5. Meaningful Comparison:
   Same embedding model for queries and chunks in shared semantic space. Vague queries may reduce retrieval quality, requiring query refinement.

6. Result Relevance:
   Generally relevant. Improvements could come from fine-tuning, hierarchical chunking, larger corpora, and query expansion.

Project Structure
-----------------

- HSC26_Bangla_1st_Paper.pdf
- main.py
- requirements.txt
- vectordb/  (persisted vector store)
- README.txt

Author: Shykul Islam Siam


