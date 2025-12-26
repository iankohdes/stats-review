# Statistics Review

Review of statistical concepts using simulation.

## Set up virtual environment

First, make sure the `uv` Python package manager is installed. I installed mine using `cargo` since I already have Rust installed.

Next, activate the environment.

```bash
>>> uv venv
Using CPython 3.13.3 interpreter at: /opt/homebrew/opt/python@3.13/bin/python3.13
Creating virtual environment at: stats-review
Activate with: source .venv/bin/activate
```

Note that it’s also possible to type `uv venv some-folder`, which creates the virtual environment as well as a folder called `some-folder`. If we leave the folder argument empty (as we did above), `uv` creates a virtual environment and uses the existing folder level as the environment name. In this case that would be `stats-review`.

After activating the environment, one should see the environment mentioned above the CLI prompt:

```bash
(stats-review)
>>> 
```

To deactivate the environment, type this:

```bash
>>> deactivate
```

## Initialise the `uv` project and add libraries

```bash
>>> uv init
Initialized project `stats-review`
>>> uv add pandas altair seaborn numpy jupyterlab
```

Failing to initialise the `uv` project results in the following error:

```bash
error: No `pyproject.toml` found in current directory or any parent directory
```

## Run JupyterLab

```bash
uv run jupyter lab
```

Note the syntax difference: when adding the library to the environment we type `jupyterlab` and, when running, we type `jupyter lab`.