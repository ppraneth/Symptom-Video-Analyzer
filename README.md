# Symptom-Video-Analyzer 🩺

Symptom-Video-Analyzer is a personal project designed to provide quick and comprehensive insights into various symptoms and health conditions. It achieves this by integrating advanced **Natural Language Processing (NLP)** with **YouTube's vast video library**. Users can simply describe a symptom, and the application will intelligently identify the core condition, find relevant educational videos, summarize their content, and extract actionable information on prevention and potential treatments. All results are presented in a user-friendly and interactive web interface powered by **Gradio**.

## ✨ How It Works

The application follows a multi-step process to deliver relevant information:

1.  **Symptom Understanding (AI Classification)**:
    * Your input (e.g., "I have a headache" or "What is diabetes?") is processed by a Hugging Face **Zero-Shot Classification model** (`facebook/bart-large-mnli`).
    * This model intelligently identifies the most relevant symptom or medical condition from a broad internal list of over 400 possibilities, even if your exact words aren't in the list.

2.  **YouTube Video Discovery**:
    * Using the identified symptom, the application queries the **YouTube Data API** to find highly relevant educational and informational videos. It fetches up to 25 videos to ensure a wide range of perspectives.

3.  **Transcript Extraction**:
    * For each found video, the application attempts to retrieve its **full spoken transcript**. This step is crucial as it converts video content into text that can be processed by NLP models.

4.  **AI-Powered Summarization & Insight Extraction**:
    * The extracted transcripts are then fed into a Hugging Face **Text Summarization model** (`facebook/bart-large-cnn`).
    * This model generates a concise overview of the video's content.
    * Crucially, the summarizer is also prompted to extract specific information related to **prevention tips** and **potential cure/treatment options** that are present within the video's transcript.

5.  **Interactive Presentation**:
    * All the gathered information—including video thumbnails, titles, the AI-generated summary, prevention tips, and cure/treatment details—is elegantly displayed.
    * An **embedded YouTube video player** is included for each result, allowing you to watch the relevant content directly within the application.

## 🛠 Technologies & Models Used

* **Python**: The core programming language.
* **Hugging Face Transformers**:
    * `facebook/bart-large-mnli`: For **Zero-Shot Text Classification**.
    * `facebook/bart-large-cnn`: For **Abstractive Text Summarization**.
* **Gradio**: For rapidly building the interactive and user-friendly web interface.
* **Google API Client (`googleapiclient`)**: To interact with the YouTube Data API.
* **`youtube-transcript-api`**: For robust extraction of video transcripts.

---
