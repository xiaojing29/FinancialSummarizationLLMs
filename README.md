# Automating Financial Text Summarization with LLMs

This project investigates parameter-efficient fine-tuning of small large language models (LLMs) for summarizing earnings call transcripts using QLoRA. It demonstrates how small models can achieve competitive performance in the financial domain with limited computational resources.

> **Course**: NLP for Finance  
> **Institution**: University of Zurich (Fall Semester 2024)

---

## Project Structure

- `notebooks/` — Fine-tuning and evaluation notebooks (Phi-3.5 and LLaMA-3.2)
- `Project Report` — Final written report detailing methodology and results

---

## Models Used

- [`microsoft/Phi-3.5-mini-instruct`](https://huggingface.co/microsoft/Phi-3.5-mini-instruct) — 3.8B parameters
- [`meta-llama/Llama-3.2-1B-Instruct`](https://huggingface.co/meta-llama/Llama-3.2-1B-Instruct) — 1B parameters

Both models support 4-bit quantization and 128k context length.

---

## Methods

- **QLoRA**: 4-bit Quantized Low-Rank Adaptation for efficient fine-tuning  
- **Instruction-format prompting** for summarization  
- Evaluation metrics:
  - ROUGE-1, ROUGE-2, ROUGE-L (lexical overlap)
  - BERTScore (semantic similarity)

---

## Dataset

- **Source**: Public dataset from Hugging Face (~2,400 earnings call transcripts)
- **Gold summaries**: Bullet-style performance summaries
- **Filtered due to memory constraints**:
  - Phi-3.5: 125 samples
  - LLaMA-3.2: 227 samples  
  (≤2048 tokens per document, no truncation used)

---

## Usage

### Run on Google Colab

Open the notebooks in the `notebooks/` directory.  
Ensure GPU runtime is enabled and required libraries are installed.

## Results

| Model                | ROUGE-1 | ROUGE-2 | ROUGE-L | BERTScore |
|---------------------|---------|---------|---------|-----------|
| Phi-3.5 (Test set)   | 0.11    | 0.04    | 0.08    | 0.82      |
| LLaMA-3.2 (Test set) | 0.11    | 0.03    | 0.07    | 0.82      |

- Both models produced semantically accurate summaries (high BERTScore) despite low lexical overlap (ROUGE) due to style mismatch with gold summaries.
- Phi-3.5 generated more concise outputs; LLaMA-3.2 was slightly better at capturing key financial metrics.

## Key Insights

- Small models fine-tuned with QLoRA can perform competitively on domain-specific summarization tasks.
- BERTScore is a more appropriate metric than ROUGE for evaluating style-divergent summaries.
- This approach enables financial NLP under limited GPU or memory resources.

## License

This repository is for educational and non-commercial research use only.
No proprietary data is included or redistributed.