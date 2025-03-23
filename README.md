# CURIE: Evaluating LLMs On Multitask Scientific Long Context Understanding and Reasoning

Evaluation Code accompanying the paper

[**CURIE: Evaluating LLMs On Multitask Scientific Long Context Understanding and Reasoning**](https://arxiv.org/abs/2503.13517)    
[ICLR 2025](https://iclr.cc/Conferences/2025)    
[arxiv](https://arxiv.org/abs/2503.13517)

> **TL;DR:** we introduce CURIE (Scientific Long **C**ontext **U**nderstanding **R**easoning and **I**nformation **E**xtraction), benchmark with 10 tasks from 6 science domains specifically designed to test the ability of LLMs to assist scientists in realistic workflows.

<img src="curie_dist.png" alt="CURIE benchmark encompasses 10 tasks, with a total of 580 input and solution pairs based on 429 research documents across six
diverse scientific disciplines: materials science, theoretical condensed matter physics, quantum computing, geospatial analysis, biodiversity, and proteins – covering both experimental and theoretical aspects of scientific research. The average length of the input queries in CURIE is about 15k words, and the ground truth responses contain on average 954 words." style="zoom:67%;" />

## 🗄️ Data

Our data is organized into eight domain-specific subfolders: "biogr", "dft", "pdb", "geo", "mpve", "qecc_65", "hfd", and "hfe".  Each subfolder contains two further subfolders: "ground_truth" and "inputs".  Within these, each data instance is stored in a JSON file named record_id.json, where record_id is a unique identifier. The "biogr" domain also includes image inputs as record_id.png files alongside the corresponding JSON.

```bash
data
    ├── domain
        ├── inputs
        │   └── record_id.json
        └── ground_truth
            └── record_id.json
    └── difficulty_levels.json

```

Ground truth data varies in structure and content across domains, but all files consistently include a record_id field matching the filename.  Input files have a uniform structure across all domains, containing both a record_id field and a text field representing the input text to LLMs.

For the "biogr" (geo-referencing) task, for 114 of the 138 examples, we release additional data including the PDF papers that each image was taken from along with other metadata in this Github repo: [https://github.com/google-research/ecology-georeferencing](https://github.com/google-research/ecology-georeferencing)

## 🧪 Running Inference.
Example Colab notebook hat runs inference by iterating over all examples and prompts for all tasks is provided at code/curie_inference.ipynb.
To execute it:
Add your API key for the model.
Connect to the default runtime ("Python 3 Google Compute Engine backend").
In the "params" cell, configure the following:
root_path: Path to the data folder.


## 🧪 Running eval.
Our evaluation Colab notebook is provided at code/curie_run_eval.ipynb. To execute it:
Connect to the default runtime ("Python 3 Google Compute Engine backend").
In the "params" cell, configure the following:
root_path: Path to the data folder.
domain: The target domain (e.g., "biogr", "dft").
llm: The Large Language Model to evaluate.
prompt: The prompt used for the LLM.
record_id: The ID of the record to evaluate.
Run the Colab.  Evaluation metrics will be printed at the end of the notebook.

Note: Evaluating the "dft" and "mpve" tasks using the LLMSim score requires querying LLMs and therefore requires setting up a Google API key.


## 📊 Generating tables and plots.

To generate the tables and plots in the paper use the notebook code/curie_generate_tables_figures.ipynb

## 📝 TODOs

- [ ] Release responses by baselines to fully reproduce the reported numbers.
- [x] Add folder with data.
- [x] Update evals to include all metrics.
- [x] Example Colab to run inference.
- [x] Colab to run evaluation.
- [x] Colab to generate all plots and tables.

## ✉️ Contact

This repository is created and maintained by [Subhashini](https://vsubhashini.github.io/). Questions and discussions are welcome under issues.

## 🙏 Acknowledgements

We are grateful to the many domain experts who have contributed to the creation
of the benchmark and evaluations.

## 📄 License

Code in this Github repository is licensed under a [APACHE 2.0 License](./LICENSE).

## 🎓 Citing CURIE

```
@inproceedings{cui2025curie,
  title={CURIE: Evaluating LLMs on Multitask Scientific Long-Context Understanding and Reasoning},
  author={Cui, Hao and Shamsi, Zahra and Cheon, Gowoon and Ma, Xuejian and Li, Shutong and Tikhanovskaya, Maria and Norgaard, Peter Christian and Mudur, Nayantara and Plomecka, Martyna Beata and Raccuglia, Paul and others},
  booktitle={The Thirteenth International Conference on Learning Representations}
  year={2025}
}
```

*This is not an officially supported Google product.*
