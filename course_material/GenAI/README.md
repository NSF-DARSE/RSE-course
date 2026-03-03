
# Generative AI Lab Notebooks

This repository contains two hands on notebooks introducing core concepts in modern Generative AI systems.

These materials were provided by the NVIDIA Deep Learning Institute and are used here for instructional and educational purposes.

---

## Notebook 1: Introduction to Generative AI with Hugging Face

This notebook provides a practical introduction to Generative AI across multiple modalities.

Topics covered include:

* Text generation using GPT style language models
* Neural machine translation
* Image generation with Stable Diffusion
* Audio generation using text to speech
* Speech transcription using Whisper

Students experiment directly with large models and explore how prompts, decoding parameters, and model architectures affect outputs. The notebook emphasizes hands on exploration and critical analysis of model behavior across text, image, and audio tasks.

By the end of this notebook, students will understand the capabilities and limitations of modern generative models and how to invoke them programmatically.

---

## Notebook 2: Retrieval Augmented Generation and Compound Systems

This notebook builds on the introduction and focuses on constructing compound AI systems around language models.

Topics covered include:

* Retrieval Augmented Generation
* Vector embeddings and similarity search
* FAISS based vector databases
* Chunking strategies for document processing
* Multi stage retrieval and reranking
* Modular orchestration using DSPy

Students learn how to combine retrieval and generation to build more reliable and scalable AI systems. The notebook emphasizes system design, orchestration patterns, and grounding techniques rather than isolated model calls.

---

## Requirements

These notebooks rely on:

* PyTorch
* Hugging Face Transformers
* Diffusers
* Sentence Transformers
* FAISS
* LangChain
* DSPy
* Whisper

They are designed to run in Google Colab, with GPU support recommended for image generation and larger language models.

---

## Attribution

Content and instructional structure for these notebooks were provided by the NVIDIA Deep Learning Institute as part of their Generative AI educational materials.
