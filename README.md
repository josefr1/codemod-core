# Codemod Core

A scalable diff-based code modification engine for HTML, CSS, and JavaScript game projects — designed for efficiency, accuracy, and minimal output size.

## 🚀 Tech Stack

- **Main language:** Python 3 (Jupyter Notebook)
- **Notebook file:** `code_generation_model.ipynb`
- **Key Libraries & Imports:**  
  `os`, `json`, `re`, `dataclasses`, `typing`, `openai`
- **Models Used:**  
  `GameCodeModifier` class (uses OpenAI GPT-based models, e.g. `gpt-4-turbo-preview`)
- **Environment Variables:**  
  Requires OpenAI API key (`OPENAI_API_KEY`)
- **Dependency Installation:**  
  Install via `pip install openai` (see notebook setup)

## ✨ Features

- Minimal search-and-replace code patches, not full file replacements
- Supports extremely large code files (10,000+ lines — 4K token limit)
- Patch output in two formats: JSON for programmatic use, Text for human-readable/debug
- Fully documented data classes: `CodePatch` and `ModificationRequest`
- Batch modification workflows
- CLI, notebook, and Colab compatibility
- Example-driven quick-start guide included in notebook

## 📁 Project Structure

- `code_generation_model.ipynb` — Main development and documentation notebook
- `README.md` — Project documentation
- *(Optionally add a requirements.txt for dependency management)*

## 🛠️ Local Development

1. **Clone the repo:**
    ```bash
    git clone https://github.com/josefr1/codemod-core.git
    cd codemod-core
    ```

2. **Install dependencies:**
    ```bash
    pip install openai
    # OR, inside notebook:
    # !pip install openai
    ```

3. **Set your API key:**
    - Get an OpenAI API key, and set it as the environment variable `OPENAI_API_KEY`.

4. **Run the notebook:**
    ```bash
    jupyter notebook code_generation_model.ipynb
    ```
    _or use Colab for step-by-step guided examples_

## 📦 Imports & Model Classes

**Core Imports:**
```python
import os
import json
import re
from typing import Dict, List, Optional, Tuple
from dataclasses import dataclass
from openai import OpenAI
```

**Key Classes:**
- `CodePatch`: Encapsulates a search/replace patch operation
- `ModificationRequest`: Encapsulates a code modification job (source, prompt, type)
- `GameCodeModifier`: The core patch engine, using OpenAI models

## ⚡ Example Usage

**Basic modification:**
```python
modifier = GameCodeModifier(api_key="YOUR_OPENAI_API_KEY")
request = ModificationRequest(
    original_code=load_code_from_file("game.html"),
    modification_prompt="Change player speed to 15 and color to blue",
    file_type="html"
)
result = modifier.modify_code(request)
if result['success']:
    save_code_to_file(result['modified_code'], "modified_game.html")
```

See notebook for advanced, batch, and preview features.

## 📝 License

This project is licensed under the [MIT License](./LICENSE).

---

_For questions or contributions, open an issue or submit a pull request!_