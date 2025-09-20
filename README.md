# A Multimodal GenAI App for Smarter Healthcare with MERaLiON

## 📌 Project Overview

This project aims to build a multimodal voice-based intelligent assistant system tailored for healthcare scenarios, especially in the local context with multiple languages in Singapore.
By integrating the MERaLiON model with H2Ogpte, the system is designed as a deployable smart application for clinics and healthcare institutions. It automatically transforms appointment and ward round recordings into structured documentation, and introduces an intelligent assistant to support doctors or healthcare institution staff to make Q&A.

### 🩺 MERaLiON
MERaLiON-2-10B is a Speech-Text large language model (AudioLLM) designed to understand and generate content from audio to text. It supports tasks like multilingual automatic speech recognition (ASR), speech translation, audio scene understanding, emotion recognition, and general speech comprehension. Its key advantage is that it’s fine-tuned for Singapore’s multilingual environment (including English, Singlish, Malay, Tamil, regional accents, etc.), and performs strongly compared with models like Whisper-large-v3, especially in local languages and code-switching scenarios.

Here is the link for the detailed information about the introduction of this model and how to import it on Huggingface.
👉 [Reference Link](https://huggingface.co/MERaLiON/MERaLiON-2-10B)

Structure of Functions
1️⃣Medical Voice Input
Applicable Scenarios:
Phone-based appointment booking / hotline consultation / in-person doctor-patient communication


Key Functions:


Record voice and upload to the backend


Use MERaLiON for Automatic Speech Recognition (ASR)


If multiple languages are involved, optionally translate to English for easier downstream processing


2️⃣Structured Document Generation
Extract key information from transcribed text, such as:


Time, symptoms, department, doctor’s advice, etc.


Automatically generate structured conversation summaries (in Markdown / JSON formats)


3️⃣ Personal Knowledge Store
Bind each patient with a unique ID to automatically create a personal document store


Store all transcripts, summaries, and doctor-uploaded formal medical reports into that patient's vector database (used for RAG)


4️⃣ Memory-Augmented Q&A
System recognizes spoken questions → converts to text → searches knowledge base (RAG) → uses LLM to generate an answer


If no answer is found locally → fallback to external LLM for response


Answers can be converted to voice via TTS, improving accessibility for elderly users


LangChain Memory + Retrieval + TTS




It is a multimodal healthcare assistant prototype that combines **Automatic Speech Recognition (ASR)**, **multilingual translation**, and **LLM-powered retrieval & structured reporting**.  
The project aims to **boost clinical productivity** and **facilitate cross-department collaboration** by converting medical dialogues into structured outputs like **SOAP notes**, **referral letters**, and **patient preview cards**.

Key objectives:
- Support **multilingual speech in Singapore context** (English, Singlish, Mandarin, Malay).  
- Reduce clinicians’ burden on **manual note-taking and summary writing**.  
- Ensure **data compliance and contextual retrieval** via patient-centric collections.  
---

## 🛠 Backend Implementation
The backend is built in **Python**, using:
- **MERaLiON ASR** for medical speech transcription.  
- **H2OGPTE** for large language model processing and RAG-based contextual retrieval.  
- **Structured output pipeline** to generate SOAP notes, referral letters, and patient summaries.  
- **Dictionary mapping** between patient IDs and collection IDs to manage case-specific data.  

👉 [Backend Code Link](./backend_code/)  

---

## 💻 Frontend Demo (Streamlit)
The frontend is implemented in **Streamlit** for an interactive demo:
- **Scenario selection**: Appointment, consultation, or ward round.  
- **Audio upload & transcription** (simulated with hardcoded text for demo).  
- **Summary display**: Auto-generated structured reports presented in the UI.  
- **Patient preview cards** for quick doctor catch-up before ward rounds.  
- **Export function** to save generated reports into files for sharing.  

👉 [Frontend Demo Code Link](./frontend_streamlit/)  

---

## 📂 Supporting Materials
For detailed design and project context, please refer to:  
- 📄 [Capstone Project Report](./Capstone_Report.pdf)  
- 🖼 [Capstone Poster](./Capstone_Poster.pdf)  

---

## 🚀 Key Takeaways
- Demonstrates the **value of combining ASR + RAG + LLM** for healthcare.  
- Improves efficiency in **clinical dialogues and reporting workflows**.  
- Provides a **scalable prototype** for real-world healthcare applications.  

---

