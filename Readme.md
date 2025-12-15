# 🎓 RAG-Based AI Teaching Assistant (Video Course Q&A)

## Project Overview
This project is a Retrieval-Augmented Generation (RAG) based AI system that enables users to ask natural-language questions about a video course and receive accurate answers with exact video numbers and timestamps.

The system converts video content into searchable knowledge by transcribing, embedding, and semantically indexing subtitles, then grounding responses using a language model.

---

## Key Features
- Semantic search over video content
- Timestamp-level answer retrieval
- Retrieval-Augmented Generation (RAG)
- Vector embedding–based indexing
- Local LLM inference
- Reusable pipeline for any video dataset

---

## Runtime Artifacts
The following files and folders are generated during execution and are intentionally excluded from the GitHub repository:
```
prompt.txt        → Generated prompt sent to the language model (for debugging)
response.txt      → Model-generated response (optional)
videos/           → Original course video files
audios/           → MP3 files generated from videos
jsons/            → Transcribed subtitle JSON files
embeddings.joblib → Generated vector embeddings for semantic retrieval
```

---

## Repository Structure (GitHub)
```
├── app.py
├── video_to_mp3.py
├── mp3_to_json.py
├── preprocess_json.py
└── README.md
```

---

## File Description

### app.py
Main inference script that:
1. Accepts a user question
2. Converts the query into an embedding
3. Retrieves relevant subtitle chunks using cosine similarity
4. Constructs a structured prompt
5. Generates a grounded response with video number and timestamp

---

### video_to_mp3.py
Converts video files into MP3 audio using FFmpeg.

---

### mp3_to_json.py
Uses the Whisper (large-v2) model to:
- Transcribe Hindi audio
- Translate it into English
- Generate timestamp-level subtitle chunks

---

### preprocess_json.py
Performs the indexing step of the RAG pipeline:
- Reads subtitle JSON files
- Generates vector embeddings using the bge-m3 model
- Serializes the embeddings into `embeddings.joblib` for efficient retrieval

---

## System Workflow
1. Video → MP3 conversion
2. MP3 → JSON transcription
3. JSON → Vector embeddings (`embeddings.joblib`)
4. User query → Embedding
5. Cosine similarity retrieval
6. LLM-based answer generation

---

## Tech Stack
- Python
- OpenAI Whisper
- Ollama (Local LLM)
- bge-m3 Embedding Model
- Pandas & NumPy
- Scikit-learn
- FFmpeg

---

## How to Run

### Step 1: Add your videos
Create a `videos/` folder and place your video files inside it.

### Step 2: Convert videos to MP3
```bash
python video_to_mp3.py
```

### Step 3: Convert MP3 to JSON
```bash
python mp3_to_json.py
```

### Step 4: Generate embeddings
```bash
python preprocess_json.py
```

### Step 5: Ask questions
```bash
python app.py
```

---

### Example Query

User Input:
Where is the input tag taught in the course?

Output:
Video number
Exact timestamp
Clear explanation of the topic

---

## 💡 Author
Shoaib  
Aspiring Data Scientist / GenAI Developer
