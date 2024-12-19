# Sideas Framework

This project implements various approaches for analyzing semantic similarity between text pairs using different models and techniques including BERT, GPT, LLaMA, and CANDC (Combinatory Categorical Grammar parser).

## Overview

The project consists of several components:

1. **CANDC Parser Integration**
   - Implementation of semantic parsing using CANDC
   - Graph-based representation of sentence structures
   - Custom similarity metrics for graph comparison

2. **Language Model Classifiers**
   - GPT-4 based similarity analysis
   - LLaMA API integration
   - BERT embeddings for semantic comparison

3. **Evaluation Framework**
   - Support for SICK dataset evaluation
   - Multiple similarity metrics (Pearson, Spearman correlations)
   - Confusion matrix and accuracy metrics

## Project Structure

```
project/
├── BERT_BASE/               # BERT model implementations
│   ├── GerarDadosValidacao/
│   └── AjusteFino/
├── CANDC/                   # CANDC parser implementation
│   ├── learningbyreading/
│   └── word2vec/
└── CLASSIFICADOR_LLM/       # Language model classifiers
    ├── GPT/
    └── LLAMA/
```

## Setup and Installation

1. Clone the repository
2. Install dependencies:
```bash
pip install python-dotenv openai llamaapi tqdm transformers torch
```

3. Set up API credentials:
   - Create a `.env` file
   - Add your API keys:
     ```
     OPENAI_API_KEY=your_key_here
     LLAMA_API_KEY=your_key_here
     ```

4. Install CANDC parser:
```bash
git clone https://github.com/valeriobasile/learningbyreading.git
cd learningbyreading/ext
./install_candc.sh
```

## Usage

### CANDC Parser Analysis

```python
from candc_parser import Graph, GraphSTS

# Create and analyze semantic graphs
graph = GraphSTS("Your input sentence here")
graph.analyze()
```

### GPT Similarity Analysis

```python
from classifier_gpt import SICKEvaluator

evaluator = SICKEvaluator(model_type="gpt", threshold=0.5)
results = evaluator.evaluate(data)
```

### LLaMA Integration

```python
from classifier_llama import LlamaSimilarityEvaluator

evaluator = LlamaSimilarityEvaluator(threshold=0.5)
results = evaluator.evaluate(data)
```

## Features

- **Graph-based Analysis**
  - Custom graph representation of sentence semantics
  - Multiple similarity metrics
  - Support for word embeddings

- **Language Model Integration**
  - GPT-4 API integration
  - LLaMA model support
  - BERT embeddings

- **Evaluation Tools**
  - Comprehensive metrics calculation
  - Support for SICK dataset
  - Confusion matrix generation

## Data Processing

The project supports various data formats:
- CSV files with sentence pairs
- SICK dataset format
- Custom input formats

Example data format:
```csv
Quality,#1 ID,#2 ID,#1 String,#2 String
1,1,2,"First sentence","Second sentence"
```

## Performance Metrics

The evaluation framework provides:
- Pearson correlation
- Spearman correlation
- Accuracy scores
- Precision metrics
- Confusion matrices

## Contributing

1. Fork the repository
2. Create your feature branch
3. Commit your changes
4. Push to the branch
5. Create a new Pull Request

## License

This project is licensed under the MIT License - see the LICENSE file for details.

## Acknowledgments

- CANDC Parser by the University of Edinburgh
- OpenAI GPT API
- LLaMA API
- BERT implementation by Hugging Face
