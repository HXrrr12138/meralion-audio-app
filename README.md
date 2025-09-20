# A Multimodal GenAI App for Smarter Healthcare with MERaLiON

## 📌 Project Overview

This project aims to build a multimodal voice-based intelligent assistant system tailored for healthcare scenarios, especially in the local context with multiple languages in Singapore.
By integrating the MERaLiON model with H2Ogpte, the system is designed as a deployable smart application for clinics and healthcare institutions. It automatically transforms appointment and ward round recordings into structured documentation, and introduces an intelligent assistant to support doctors or healthcare institution staff to make Q&A.

### 🩺 MERaLiON
MERaLiON-2-10B is a Speech-Text large language model (AudioLLM) designed to understand and generate content from audio to text. It supports tasks like multilingual automatic speech recognition (ASR), speech translation, audio scene understanding, emotion recognition, and general speech comprehension. Its key advantage is that it’s fine-tuned for Singapore’s multilingual environment (including English, Singlish, Malay, Tamil, regional accents, etc.), and performs strongly compared with models like Whisper-large-v3, especially in local languages and code-switching scenarios.

Here is the link for the detailed information about the introduction of this model and how to import it on Huggingface.
👉 [Reference Link](https://huggingface.co/MERaLiON/MERaLiON-2-10B)

### ✅ Key objectives:
- Support **multilingual speech in Singapore context** (English, Singlish, Mandarin, Malay).  
- Reduce clinicians’ burden on **manual note-taking and summary writing**.  
- Ensure **data compliance and contextual retrieval** via patient-centric collections.  
---

## 🔧 Backend Implementation

The backend is implemented in **Python** and integrates multiple AI components into a structured workflow:

### MERaLiON ASR
- Built on Hugging Face’s `MERaLiON-2-3B` model for robust medical speech transcription.  
- Supports long audio by splitting into silence-based segments (via `pydub`), then transcribing chunk by chunk for higher accuracy.  

### LangChain + H2OGPTE Integration
- A custom `H2OGPTE_LLM` wrapper connects H2OGPTE into the LangChain ecosystem.  
- Multiple `LLMChain` pipelines are defined for translation, date normalization, appointment summaries, bedside consultation summaries, and emotion-based advice generation.  

### Structured Multi-Scenario Pipelines
- **Appointment Pipeline**: Converts audio into transcript → checks language → translates if needed → standardizes dates → extracts structured JSON (patient info, symptoms, appointment time) → stores in Excel + uploads to patient’s collection.  
- **Bedside Consultation Pipeline**: Produces structured progress notes (JSON + Word template) and uploads to patient’s collection, with raw transcript stored in parallel.  
- **SOAP / Pre-briefing Generation**: Summarizes a patient’s collection into SOAP notes or concise pre-briefings for doctors.  

### Patient Data Management
- Maintains a dictionary mapping between patient IDs (NRIC) and H2OGPTE collection IDs.  
- Each pipeline automatically uploads generated summaries, transcripts, or Word notes to the correct patient collection for future retrieval.  

### Contextual Q&A with Memory
- Implements per-patient conversational memory (`ChatMessageHistory`), allowing doctors to ask follow-up questions with continuity.  
- Includes fallback logic: if retrieval fails, queries are routed to the general LLM.  

### Text-to-Speech (TTS) Extension
- Integrates with ElevenLabs API to convert LLM-generated answers into natural speech, supporting hands-free review by clinicians.  

👉 [Backend Code Link on Google Drive](https://drive.google.com/drive/folders/1SYw_cn9aqFWKevIoEMMBuXLcryTQUFAM?usp=drive_link)
The main coding part is in the file **Backend_part.ipynb**

---

## 💻 Frontend Demo (Streamlit)
The frontend of this project is built with **Streamlit**, providing an interactive interface to showcase the main features of the backend system.  
To explore how the demo works in detail, including the complete project files and usage instructions, please refer to the dedicated repository below:

👉 [Frontend Demo Code Repository](https://github.com/HXrrr12138/Streamlit-demo-app)

---

## 📂 Other Supporting Slides and Materials
For detailed design and project context, please refer to:   
- 🖼 [Capstone Poster](.Slides/Project_idea_poster.png)  

---

