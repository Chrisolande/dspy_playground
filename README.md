# DSPy Workbench

This repository serves as a hands-on workbench for demonstrating and iterating on the capabilities of the [DSPy](https://github.com/stanfordnlp/dspy) library. It provides a detailed Jupyter notebook (`dspy_workbench.ipynb`) that walks through various DSPy features, from basic setup to advanced prompt optimization and instruction tuning.

## Features Demonstrated

The `dspy_workbench.ipynb` notebook provides an annotated guide to:

- **LLM Configuration**: Setting up a DeepSeek LLM for use with DSPy.
- **Core DSPy APIs**:
  - `dspy.ChainOfThought`: For explicit, reasoning-based generation.
  - `dspy.Module`: For creating custom, composable models.
  - `dspy.Predict`: For direct, signature-based predictions.
- **Content Summarization**: Using `ChainOfThought` to summarize long documents.
- **Evaluation and Validation**:
  - Defining custom `dspy.Signature` for evaluation (e.g., `ContextualAlignment`).
  - Using `dspy.Example` and `dspy.Evaluate` to assess model performance.
- **Multi-Hop Retrieval**: Implementing a simple `Hop` module that uses `TavilySearch` for multi-step information retrieval.
- **Prompt Optimization (Teleprompting)**:
  - `LabeledFewShot`: Compiling prompts with a few-shot learning approach.
  - `BootstrapFewShot`: Bootstrapping examples to improve prompt quality.
  - `BootstrapFewShotWithRandomSearch`: Using random search to find optimal prompt structures.
- **Instruction Tuning**:
  - A practical example using `MIPROv2` to instruction-tune a PubMed query parser.
  - Using an LLM-based judge for evaluating complex, structured outputs.

## Getting Started

### Prerequisites

- Python 3.12 or higher.
- A DeepSeek API key.
- A Tavily API key (for the multi-hop search feature).

### Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/Chrisolande/dspy-playground.git
   cd dspy-playground
   ```

2. **Install dependencies:**
   This project uses Poetry for dependency management. If you don't have Poetry installed, you can find installation instructions [here](https://python-poetry.org/docs/).
   ```bash
   poetry install
   ```

3. **Set up your environment:**
   - Create a `.env` file in the root of the project.
   - Add your DeepSeek and Tavily API keys to the `.env` file:
     ```
     DEEPSEEK_API_KEY="your_deepseek_api_key_here"
     TAVILY_API_KEY="your_tavily_api_key_here"
     ```

4. **Prepare the data:**
   The notebook requires two data files:
   - `data/sliced_tweets.csv`: Used for the sentiment analysis and prompt optimization examples.
   - `data/few.csv`: Used for the instruction-tuning example.

   You will need to create a `data` directory and source these files yourself.

## Usage

Once you have completed the setup, you can explore the notebook:

1. **Activate the Poetry shell:**
   ```bash
   poetry shell
   ```

2. **Start Jupyter Lab:**
   ```bash
   jupyter lab
   ```

3. Open and run the `dspy_workbench.ipynb` notebook to see the demonstrations.

## Development

This project uses a suite of tools to ensure code quality and consistency.

### Development Dependencies

To install the development dependencies, run:
```bash
poetry install --with dev
```

The development dependencies include:
- `black`: For code formatting.
- `isort`: For sorting imports.
- `autoflake`: For removing unused imports and variables.
- `mypy`: For static type checking.
- `nbqa`: For running linters and formatters on notebooks.
- `ruff`: For linting.

### Pre-commit Hooks

This repository is configured with pre-commit hooks to automatically run these tools before each commit. To set up the hooks, run:
```bash
pre-commit install
```
