# Gene-Disease Assistant using TinyLlama

This project fine-tunes TinyLlama-1.1B-Chat on a gene-disease instruction dataset to build a lightweight assistant.
It also includes an optional retrieval-augmented generation (RAG) module for improved answer generation.

---

## Setup

1. Install dependencies:
   pip install transformers datasets peft accelerate bitsandbytes

2. Login to Hugging Face:
   huggingface-cli login

3. Place the 'gene_disease_rich.jsonl' file in the working directory.

---

## Fine-tuning

- Loads TinyLlama in 4-bit precision using bitsandbytes.
- Applies LoRA (Low-Rank Adaptation) to attention layers.
- Fine-tunes on instruction-formatted prompts.
- Saves model checkpoints after each epoch.

---

## Inference

- After training, load the model and chat using a CLI interface.
- RAG module optionally looks up relevant data to improve answers.

---

## Files

- tinyllama_tune.ipynb — Fine-tuning script
- model_inference.py — Basic inference
- rag_inference.py — RAG-based inference
- gene_disease_rich.jsonl — Dataset

---

## Example Query

🧬 You: Which genes are associated with Setleis syndrome?
🧠 Model: The genes associated with Setleis syndrome are...

## Reference 
Diamant I, Clarke DJB, Evangelista JE, Lingam N, Ma'ayan A. Harmonizome 3.0: integrated knowledge about genes and proteins from diverse multi-omics resources. Nucleic Acids Res. 2024 Nov 20. pii: 53(1):D1016-D1028.

Rouillard AD, Gundersen GW, Fernandez NF, Wang Z, Monteiro CD, McDermott MG, Ma'ayan A. The harmonizome: a collection of processed datasets gathered to serve and mine knowledge about genes and proteins. Database (Oxford). 2016 Jul 3;2016. pii: baw100.

## Note 
- The finetuned model can be found at https://huggingface.co/ftkd99/gen-dis_tinyllama
- Training required more epochs, prevalent losses are affecting the response generation.