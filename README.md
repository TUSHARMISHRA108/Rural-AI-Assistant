# 🌾 KrishiMitra AI

### Multimodal AI Assistant for Farmers

KrishiMitra AI is a project I am developing to make agricultural assistance easier to access for farmers.

The idea is simple: instead of requiring a farmer to type a technical question, the farmer can send a **crop image, voice message, text, or a combination of image and voice**.

The system processes this information and provides a farmer-friendly response using AI, agricultural knowledge retrieval, and Indian-language support.

> **Current prototype:** Telegram
> **Planned deployment:** WhatsApp

---

## Problem

Many agricultural information systems depend on text-based queries, app navigation, or users knowing how to describe their crop problem technically.

This can be difficult when a farmer wants to ask something like:

> "There are small insects under my tomato leaves and the leaves are curling. What should I do?"

The farmer may not know the name of the pest or how to describe the symptoms in technical terms.

KrishiMitra tries to make the interaction more natural:

**Take a photo → Speak the problem → Get a simple answer**

---

## What KrishiMitra Does

The current prototype supports:

* 📷 Crop image input
* 🎙️ Voice input
* 💬 Text input
* 🔎 Image-based crop problem analysis
* 🧠 AI-based response generation
* 📚 Agricultural RAG / knowledge retrieval
* 🌐 Indian-language support
* 🔊 Voice-based response support
* 🔄 LLM fallback mechanism

---

## System Architecture

![KrishiMitra AI Architecture](architecture/system_architecture.png)

### Current AI Pipeline

```text
             FARMER
                │
       ┌────────┼────────┐
       │        │        │
     Image    Voice     Text
       │        │        │
       ▼        ▼        ▼
   Gemini    Groq     Text Processing
   Vision    Speech
       │        │
       └────┬───┘
            ▼
      Multimodal Context
            │
            ▼
    Agricultural RAG
            │
            ▼
 Agricultural Knowledge Base
            │
            ▼
      Response Generation
            │
      ┌─────┴─────┐
      │           │
    Groq      OpenRouter
  Primary      Fallback
      │           │
      └─────┬─────┘
            ▼
        Bhashini
            │
            ▼
   Indian Language / Voice
            │
            ▼
          Farmer
```

---

## Technologies Used

| Component           | Technology            | Purpose                                    |
| ------------------- | --------------------- | ------------------------------------------ |
| Image Analysis      | Gemini                | Crop image understanding                   |
| Voice Processing    | Groq / Whisper        | Voice-to-text processing                   |
| Primary Response    | Groq                  | Response generation                        |
| Fallback            | OpenRouter            | Backup LLM route                           |
| Knowledge Retrieval | RAG                   | Retrieve relevant agricultural information |
| Vector Search       | FAISS                 | Similarity-based retrieval                 |
| Embeddings          | Sentence Transformers | Convert agricultural text into vectors     |
| Language Layer      | Bhashini              | Indian-language translation / speech       |
| Interface           | Telegram              | Current working prototype                  |
| Planned Interface   | WhatsApp              | Easier farmer access                       |

---

## Agricultural Knowledge Base

The RAG component is intended to ground responses in agricultural information rather than relying only on the LLM's internal knowledge.

The knowledge base is being structured around:

* Crops
* Pests
* Diseases
* Nutrient deficiencies
* Symptoms
* Organic management
* Prevention
* Crop treatments
* Farmer-used terms / synonyms
* Source documents
* Page-level references

### Current limitation

The current agricultural knowledge base is still relatively small.

Therefore, KrishiMitra cannot reliably answer every possible agricultural question yet.

One of my current goals is to expand the knowledge base using verified agricultural documents and improve retrieval and evaluation.

---

## Example

### Farmer Input

**Image:** Tomato leaves with small insects

**Voice:**

> "There are many small insects under the leaves and the leaves are curling. What organic solution can I use?"

### Processing

1. Gemini analyses the crop image.
2. Voice is converted into text.
3. The image information and farmer description are combined.
4. Relevant agricultural information is retrieved from the RAG knowledge base.
5. The response is generated.
6. Bhashini can provide the response in an Indian language / voice format.

### Expected Output

A simple farmer-friendly explanation of the likely problem, relevant symptoms, and evidence-based management options.

---

# Why not just use ChatGPT or Gemini?

KrishiMitra is not intended to compete with general-purpose LLMs by claiming to have a larger or smarter model.

Instead, the goal is to build a **domain-specific system around existing AI models**.

A general LLM can answer agricultural questions, but KrishiMitra is designed around a specific farmer workflow:

```text
Photo + Voice
      ↓
Agricultural Context
      ↓
Agricultural Knowledge Retrieval
      ↓
AI Reasoning
      ↓
Local Language
      ↓
Farmer-Friendly Response
```

The system can also be extended with agriculture-specific services such as:

* Mandi prices
* Regional crop-problem monitoring
* Repeated-query detection
* Local agricultural information

The research question I am interested in is whether this domain-specific workflow can provide more useful and better-grounded assistance than simply asking a general-purpose LLM.

---

## Current Prototype

The current working prototype is available through **Telegram**.

The core workflow is functional, including:

* Image input
* Voice input
* Text input
* AI processing
* RAG retrieval
* LLM fallback
* Indian-language processing

The system is still under development.

---

## Current Limitations

The project is currently a prototype, not a production agricultural advisory system.

Current limitations include:

1. The agricultural knowledge base is still small.
2. Retrieval quality needs further evaluation.
3. Crop diagnosis can be uncertain when image quality is poor.
4. Different crop diseases and pests can have similar visual symptoms.
5. The system needs a larger evaluation dataset.
6. Real-world farmer testing is still required.

These limitations are part of the current development and research work.

---

## Future Work

### 1. Larger Agricultural Knowledge Base

Expand the verified knowledge base across major Indian crops.

### 2. Better Multimodal Evaluation

Compare:

* Image-only input
* Voice-only input
* Text-only input
* Image + voice input

and measure whether combining modalities improves diagnosis.

### 3. Response Evaluation

Evaluate:

* Accuracy
* Relevance
* Retrieval quality
* Hallucination/error rate
* Source grounding
* Uncertainty handling

### 4. Mandi Information

Integrate relevant market-price information to provide additional decision support.

### 5. Regional Pattern Detection

If many similar crop-related questions are received from a particular geographical area, the system could identify a possible regional pattern and generate an alert for further investigation.

### 6. WhatsApp Deployment

Move the farmer-facing interface from the current Telegram prototype to WhatsApp to reduce the need for farmers to install and learn a separate application.

---

## Project Status

| Component                   | Status              |
| --------------------------- | ------------------- |
| Telegram Bot                | ✅ Working prototype |
| Image Input                 | ✅ Working           |
| Voice Input                 | ✅ Working           |
| Text Input                  | ✅ Working           |
| Gemini Image Analysis       | ✅ Integrated        |
| Groq Processing             | ✅ Integrated        |
| OpenRouter Fallback         | ✅ Integrated        |
| RAG Pipeline                | 🚧 Developing       |
| Agricultural Knowledge Base | 🚧 Expanding        |
| Bhashini Integration        | ✅ Integrated        |
| Mandi Data                  | 🔜 Planned          |
| Regional Pattern Detection  | 🔜 Planned          |
| WhatsApp Deployment         | 🔜 Planned          |

---

## Research Direction

The long-term goal is not simply to build another agricultural chatbot.

I want to investigate how **multimodal machine learning + retrieval-augmented generation + domain-specific knowledge** can be combined to build more reliable AI assistance for real-world agricultural problems.

A particular area I am interested in is comparing **image-only crop diagnosis with image + voice diagnosis** and studying whether additional contextual information from the farmer improves the quality and reliability of the result.

---

## Disclaimer

KrishiMitra AI is currently a research/prototype project.

Its responses should not be treated as a substitute for advice from qualified agricultural experts. The system may produce incorrect or incomplete results, particularly when the available evidence or knowledge-base coverage is insufficient.
