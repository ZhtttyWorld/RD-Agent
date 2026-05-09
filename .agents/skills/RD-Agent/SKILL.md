```markdown
# RD-Agent Development Patterns

> Auto-generated skill from repository analysis

## Overview

This skill teaches you the core development patterns, coding conventions, and key workflows for contributing to the **RD-Agent** repository. RD-Agent is a Python project built with Flask, focused on scenario-driven agent development, including LLM finetuning, RL benchmarking, and Qlib experiments. The repository features modular scenario logic, prompt engineering, and a web frontend, with a strong emphasis on reproducible workflows and maintainable code.

## Coding Conventions

- **File Naming:**  
  Use `snake_case` for all Python files and directories.  
  *Example:*  
  ```
  rdagent/scenarios/finetune/benchmark/data_loader.py
  ```

- **Import Style:**  
  Mixed usage of absolute and relative imports.  
  *Example:*  
  ```python
  import os
  from rdagent.components.utils import load_config
  from .proposal import generate_proposal
  ```

- **Export Style:**  
  Mixed; some modules use explicit `__all__`, others rely on implicit exports.  
  *Example:*  
  ```python
  __all__ = ["generate_proposal", "evaluate_benchmark"]
  ```

- **Commit Messages:**  
  Use [Conventional Commits](https://www.conventionalcommits.org/), with prefixes like `fix`, `feat`, `chore`, `docs`.  
  *Example:*  
  ```
  feat: add new RL benchmark for AutoRL-Bench
  fix: correct data loader bug in finetune scenario
  ```

## Workflows

### Dependency Update Web
**Trigger:** When a dependency in the web frontend needs to be updated (security, bugfix, or routine maintenance).  
**Command:** `/update-web-deps`

1. Update `web/package.json` with new dependency version(s).
2. Update `web/package-lock.json` to lock new versions.
3. Commit both files with a message referencing the dependency and version.

*Example commit:*
```
chore: bump react to 18.2.0 in web frontend
```

---

### Add or Update Benchmark or Dataset
**Trigger:** When a new benchmark or dataset is integrated, or an existing one is updated for evaluation or training.  
**Command:** `/add-benchmark`

1. Add or update files in:
    - `rdagent/scenarios/finetune/benchmark/`
    - `rdagent/scenarios/finetune/datasets/`
    - `rdagent/scenarios/rl/autorl_bench/benchmarks/`
2. Add or update `README.md` or `description.md` for the benchmark/dataset.
3. Update configs (e.g., `models.yaml`, `opencompass_template.yaml`).
4. Update or add evaluation scripts (`eval.py`, `data.py`, etc.).
5. Update UI or summary code if needed.

*Example directory structure:*
```
rdagent/scenarios/finetune/benchmark/my_benchmark/
  ├── data.py
  ├── eval.py
  ├── configs/
  └── description.md
```

---

### Scenario Feature Development Loop
**Trigger:** When a new scenario or major feature is being built or significantly extended.  
**Command:** `/new-scenario`

1. Implement or update scenario loop and core logic (e.g., `loop.py`, `conf.py`, `scen.py`).
2. Add or update prompts and proposal logic (`prompts.yaml`, `proposal.py`).
3. Add or update UI files (`ui/app.py`, `ui/components.py`, `web/src/views/`).
4. Add or update config files and requirements (`requirements.txt`, `Dockerfile`, `.env.example`).
5. Add or update documentation (`README.md`, `docs/`).
6. Add or update tests if needed.

*Example:*
```python
# rdagent/scenarios/finetune/loop.py
def run_finetune_loop(config):
    # core logic here
    pass
```

---

### Qlib Experiment Template Update
**Trigger:** When Qlib experiment structure or configuration needs to be updated for new features or refactoring.  
**Command:** `/update-qlib-template`

1. Update YAML config files for Qlib experiments (e.g., `conf_baseline.yaml`).
2. Update runner scripts (`factor_runner.py`, `model_runner.py`).
3. Update experiment logic (`factor_experiment.py`, `model_experiment.py`).
4. Update documentation if needed.

*Example:*
```
rdagent/scenarios/qlib/experiment/factor_template/conf_baseline.yaml
rdagent/scenarios/qlib/experiment/factor_runner.py
```

---

### Prompt and Proposal Improvement
**Trigger:** When prompt templates or proposal logic need to be improved for better agent performance or new features.  
**Command:** `/improve-prompt`

1. Edit or add `prompts.yaml` files in relevant scenario/component directories.
2. Update `proposal.py` or related logic to use new prompts or handle new response formats.
3. Update or add documentation if needed.

*Example:*
```yaml
# rdagent/components/coder/llm/prompts.yaml
- role: system
  content: |
    You are an expert code reviewer...
```

## Testing Patterns

- **Framework:** Unknown (no standard Python testing framework detected).
- **File Pattern:** Some tests use `*.test.ts` (TypeScript), likely for the web frontend.
- **Python Tests:** If adding Python tests, follow the `test_*.py` convention and use `pytest` or `unittest`.

*Example:*
```python
# test_data_loader.py
def test_load_data():
    assert load_data("sample.csv") is not None
```

## Commands

| Command              | Purpose                                                          |
|----------------------|------------------------------------------------------------------|
| /update-web-deps     | Update JavaScript/TypeScript dependencies in the web frontend    |
| /add-benchmark       | Add or update a benchmark or dataset for a scenario              |
| /new-scenario        | Start a new scenario or major feature development loop           |
| /update-qlib-template| Update Qlib experiment templates and configuration               |
| /improve-prompt      | Refine or add prompt templates and proposal logic                |
```
