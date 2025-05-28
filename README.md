# Evaluating Modern Retrieval-Augmented Generation (RAG) Systems 

**Author:** Apostolos Falaras

**Thesis:** Undergraduate Thesis in Electrical & Computer Engineering

**University:** University of Thessaly

**Supervisor:** Prof. Manolis Vavalis

**Thesis Conducted:** October 2024 - February 2025


## 📚 Overview

This repository contains the code and evaluation results of my Undergraduate Thesis on **Retrieval-Augmented Generation (RAG)** systems. The project investigates how effectively modern RAG frameworks evaluate Generative AI systems across both **general-purpose** and **legal** domains.


## 🎯 Objective

The goal of this thesis was:
- Analyze and compare state-of-the-art RAG evaluation frameworks: **RAGChecker**, **RAGAs**, **ARES**, and **AutoRAG**
- Apply them to a RAG pipeline combining retriever and generator components
- Evaluate performance on two datasets:
    -  **MS MARCO** (generic knowledge)
    -  **LegalBench-RAG** (domain-specific legal data)
- Use **Chroma** and **SQLiteVec** as both the **vector store and retriever**, depending on the dataset:
    - **Chroma** was used for the MS MARCO pipeline
    - **SQLiteVec** was used for the LegalBench-RAG pipeline


## 🧠 Background

LLMs are increasingly being deployed in knowledge-intensive domains, yet they often face:
- Outdated or incomplete training data
- Inability to ground responses in real-time information

RAG systems solve this by combining:
- **Retrievers**: Find relevant external passages based on the query
- **Generators**: Answer the query using retrieved context and model knowledge


## ⚙️ Project Structure

- `RAG_Evaluation_MS_MARCO.ipynb` — evaluation on general dataset (MS MARCO)
- `RAG_Evaluation_LegalBench-RAG.ipynb` — evaluation on legal dataset
- `Falaras_Apostolos_Thesis_Report.pdf` — full thesis report detailing architecture, literature review, evaluation, and results
- `requirements.txt` — list of Python packages required


## 🧪 Evaluation Frameworks Used

| Framework    | Focus Area                                                          | Open Source  |
| ---------------- | ------------------------------------------------ | ----------------- |
| RAGChecker | Fine-grained claim-based retrieval and generation evaluation    |  ✅ |  
| RAGAs             | LLM-based faithfulness, context and answer relevance scores | ✅ |
| ARES                | Automated evaluation with synthetic data and LLM judges of faithfulness, context and answer relevance | ✅ |
| AutoRAG        | Modular pipeline evaluation with built-in retrievers, rerankers and generators | ✅ | 

Each notebook demonstrates how these tools were used and compares their effectiveness.


## 📊 Datasets

- **MS MARCO v1.1**  
  Loaded directly from [Hugging Face Datasets](https://huggingface.co/datasets/microsoft/ms_marco) using the `datasets` library.  
  The dataset is programmatically downloaded and cached in `.arrow` format via:

  ```python
  from datasets import load_dataset
  ms_marco = load_dataset("microsoft/ms_marco", "v1.1", cache_dir="./Datasets/", trust_remote_code=True)
  ```

- **LegalBench-RAG**  
  The legal dataset used in this project was obtained from a Dropbox link shared via the official [LegalBench GitHub repository]([https://github.com/HazyResearch/legalbench](https://github.com/zeroentropy-ai/legalbenchrag?tab=readme-ov-file)).  
  It includes legal-domain QA tasks designed to benchmark retrieval-augmented legal reasoning systems.

📝 These datasets were used for academic evaluation purposes only. Please refer to the original dataset providers for license and usage details.


## ⚠️ Notes on Framework Execution Challenges

During the evaluation of the **MS MARCO** dataset, the **ARES** and **AutoRAG** frameworks could not be executed successfully, despite separate environment setup and input preparation.

- **ARES** was tested in a dedicated conda environment to avoid dependency conflicts (notably with `datasets` and `ragchecker`). Although some internal code was patched (`load_metric` → `load`), the evaluation did not complete, possibly due to additional internal constraints or incompatibilities, or limitations in the way I applied it.

- **AutoRAG** was also run in a separate conda environment. While inputs were formatted as expected, the evaluation failed at runtime — potentially due to undocumented assumptions, configuration mismatches, or limitations in the way I applied it.

These outcomes may not fully reflect the frameworks’ capabilities, but rather real-world integration challenges and time constraints typical in academic research.

📎 The full logs and diagnostic attempts are available in Section 6 of [`RAG_Evaluation_MS_MARCO.ipynb`](./RAG_Evaluation_MS_MARCO.ipynb), included to support transparency and future debugging by other users or contributors.


## 📈 Key Findings

- RAGChecker offered detailed insights into noise sensitivity and hallucination rates
- RAGAs used LLM prompting to assess contextual and factual grounding
- Domain-specific legal queries showed greater variance across tools, emphasizing the importance of dataset quality and chunking methods
- Legal RAG pipelines are more sensitive to chunk size, embedding model, and retriever precision


## 💡 Future Work

- Extend benchmarking to more legal subdomains
- Incorporate memory and re-ranking modules
- Evaluate performance over multilingual datasets

## 🔧 How to Run

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/rag-evaluation-thesis.git
   cd rag-evaluation-thesis
   ```

2. Install the required Python libraries:
   ```bash
   pip install -r requirements.txt
   ```

3. Launch the notebooks:
   ```bash
   jupyter notebook
   ```
   *(or use `jupyter lab` if you prefer the JupyterLab interface)*

4. Run the notebooks in order:
   - `RAG_Evaluation_MS_MARCO.ipynb`
   - `RAG_Evaluation_LegalBench-RAG.ipynb`

📝 Note: Some evaluation tools (like ARES and AutoRAG) require separate virtual environments due to dependency conflicts. See Section 6 in the MS MARCO notebook for details.


## 📄 License

This project is shared publicly to document my academic work, showcase technical skills, and support others working in similar areas.

It is licensed for **non-commercial, academic, and educational use only**.  
Commercial use, redistribution, or integration into proprietary software is **not permitted** without express written permission from the author.

If you are interested in using this work in a commercial context, please contact me.


## 📑 Citation

```
@thesis{falaras2025rag,
  title={Evaluating Modern Retrieval-Augmented Generation (RAG) Systems},
  author={Falaras, Apostolos},
  year={2025},
  institution={University of Thessaly}
}
```

⚠️ This thesis project reflects my independent implementation and experimentation (Oct 2024 – Feb 2025). Community feedback and respectful reuse in research are welcome.





