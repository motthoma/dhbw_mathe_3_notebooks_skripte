# Mathematik 3 – Differential Equations

Python scripts and notebooks for the Mathematik 3 course at DHBW.

## Set up the Python environment

This project uses [uv](https://docs.astral.sh/uv/) to manage Python and its
dependencies. Python 3.12 is selected in `.python-version`; the dependencies
are declared in `pyproject.toml` and their resolved versions are in `uv.lock`.

### 1. Install uv

On Linux or macOS:

```sh
curl -LsSf https://astral.sh/uv/install.sh | sh
```

On Windows (PowerShell):

```powershell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```

Restart your terminal after installation, then check that uv is available:

```sh
uv --version
```

For other installation options, see the [uv installation guide](https://docs.astral.sh/uv/getting-started/installation/).

### 2. Create and synchronize the environment

Open a terminal in this repository's root directory (the directory containing
`pyproject.toml`) and run:

```sh
uv sync --locked
```

This downloads Python 3.12 if needed, creates the local `.venv` environment,
and installs the project and its dependencies, including NumPy, SciPy,
Matplotlib, and ipykernel. An existing `.venv` is synchronized instead.
The first setup requires internet access. `--locked` keeps the versions in
`uv.lock` and reports an error if the lockfile is out of date.

### 3. Verify and use the environment

Check Python and the installed dependencies:

```sh
uv run --locked python --version
uv run --locked python -c "import numpy, scipy, matplotlib, ipykernel; print('Environment ready')"
```

Run a script from the repository root:

```sh
uv run --locked python scripts/explicit_euler.py
```

`uv run` uses the project's environment automatically, so activation is
optional. To activate it manually in Bash or Zsh:

```sh
source .venv/bin/activate
```

Or in Windows PowerShell:

```powershell
.venv\Scripts\Activate.ps1
```

Use `deactivate` to leave an activated environment.

For notebooks such as `scripts/explicit_euler.ipynb`, select the Python
interpreter in `.venv` as the kernel in your notebook editor (for example,
VS Code with the Python and Jupyter extensions).

After pulling dependency changes, run `uv sync --locked` again. See the
[uv project guide](https://docs.astral.sh/uv/guides/projects/) for more details.
