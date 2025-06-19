# Automating Financial Text Summarization with LLMs

This project explores parameter-efficient fine-tuning of small large language models (LLMs) to summarize earnings call transcripts using QLoRA.

> **Course**: NLP for Finance, University of Zurich (Fall Semester 2024)

---

## Project Structure

- `notebooks/` — Fine-tuning and evaluation notebooks (Phi-3.5 and LLaMA-3.2)
- `Project Report` — Final written report detailing methodology and results

---

## Models Used

- [`microsoft/Phi-3.5-mini-instruct`](https://huggingface.co/microsoft/Phi-3.5-mini-instruct)
- [`meta-llama/Llama-3.2-1B-Instruct`](https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct)

---

## Methods

- Fine-tuning with **QLoRA** (Quantized Low-Rank Adaptation)
- Prompt-based instruction format for summarization
- Evaluation metrics: **ROUGE** and **BERTScore**

---

## Dataset

- Public dataset from Hugging Face (~2,400 earnings call transcripts with bullet-point summaries)
- Token-limited selection due to memory constraints:
  - **Phi-3.5**: 125 samples (≤2048 tokens)
  - **LLaMA-3.2**: 227 samples (≤2048 tokens)

---

## Usage

### Run in Google Colab

Open the notebooks under the `notebooks/` directory.  
Make sure to install the required libraries and configure a GPU runtime.

---

## Results

- **BERTScore**: 0.82
- **ROUGE-1**: 0.11  
- The models generated summaries that were **semantically accurate** but **stylistically different** from the reference telegraph-style bullet points.

---

## License

This project is for academic and demonstration purposes only.  
No proprietary data is used or distributed.

