This project implements a Retrieval-Augmented Generation (RAG) system powered by LLaMA3, enabling efficient querying of multiple document types, such as PDFs, Excel sheets, PowerPoint presentations, and Word documents. The system is designed for offline use, ensuring data privacy while providing accurate, context-aware responses.

Features
Query data from PDFs, Excel files, PowerPoint presentations, and Word documents.
Provides accurate, context-aware natural language responses using the LLaMA3 model.
Implements efficient text chunking, embedding, and retrieval using FAISS.
Designed for offline deployment, ensuring no external dependencies or internet connectivity.

Setup Instructions
Step 1: Prerequisites
Ensure you have access to the target machine with 64-bit architecture.
Make sure Conda is installed on your system. If not, download and install Anaconda.

How to Package the environment?
1. install conda-pack
2. conda install -c conda forge conda-pack

Create a portable package:
conda pack -n packaged_env -o packaged_env.tar.gz
This command creates a file(packaged_env.tar.gz) that contains the Python interpreter, all libraries etc.

Step 2: Setting Up the Packaged Environment
The project uses a pre-packaged Conda environment called packaged_env. Follow the steps below to set it up on the target machine:

Copy the environment file to the target machine:

Transfer the packaged_env.tar.gz file to the target machine.
Extract and Set Up the Environment:

Open a terminal or command prompt on the target machine and navigate to the directory containing the packaged_env.tar.gz file.
Run the following commands:
bash
Copy code
tar -xvzf packaged_env.tar.gz
conda env create -f packaged_env.yml
Activate the Environment:

bash
Copy code
conda activate packaged_env
Verify the Environment: Check if the environment is working correctly:

bash
Copy code
python --version
The Python version should match the one used during development (e.g., Python 3.9).

Step 3: Running the Project
Transfer the project files, including the main Python script (e.g. rag90.py) and the input documents (PDFs, Excel sheets, etc.), to the target machine.

Run the main script:

bash
Copy code
python rag_system.py
Interact with the system by entering your query when prompted:

Example:
plaintext
Copy code
Enter your query: What is covered in the AI notes?
Response: [Generated response based on the input documents]
How It Works
Data Loading:

Extracts text from multiple document types:
PDFs: Processes text using pdfplumber.
Excel Sheets: Reads and converts rows into textual chunks using pandas.
PowerPoint Presentations: Extracts text from slides using python-pptx.
Embedding Generation:

Text chunks are converted into embeddings using SentenceTransformers (all-MiniLM-L6-v2).
Efficient Retrieval:

FAISS is used to store and search embeddings for relevant chunks based on the query.
Response Generation:

Relevant chunks are passed to the LLaMA3 model to generate accurate and context-aware responses.


