# Statistics Review

Review of statistical concepts using simulation.

## Set up virtual environment

First, make sure the `uv` Python package manager is installed. I installed mine using `cargo` since I already have Rust installed.

Next, activate the environment.

```bash
> uv venv
Using CPython 3.13.3 interpreter at: /opt/homebrew/opt/python@3.13/bin/python3.13
Creating virtual environment at: stats-review
Activate with: source .venv/bin/activate
```

Note that it’s also possible to type `uv venv some-folder`, which creates the virtual environment as well as a folder called `some-folder`. If we leave the folder argument empty (as we did above), `uv` creates a virtual environment and uses the existing folder level as the environment name. In this case that would be `stats-review`.

After activating the environment, one should see the environment mentioned above the CLI prompt:

```bash
(stats-review)
> 
```

To deactivate the environment, type this:

```bash
> deactivate
```

## Initialise the `uv` project and add libraries

```bash
>>> uv init
Initialized project `stats-review`
> uv add pandas altair seaborn numpy jupyterlab
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

## Render Altair plots in PNG format

Altair’s plots are rendered with JavaScript by default, but this is disabled in GitHub and GitLab (likely for security reasons). The result is that any plots made with this library are viewable in a Jupyter notebook but _not_ viewable once it’s pushed to the remote repository.

Here’s what I tried to make my plots viewable in GitHub.

```bash
> uv add vl-convert-python vega
```

(I’m not sure if `vega` is truly required, so feel free to experiment with omitting it.)

Inside JupyterLab, run this command:

```
alt.renderers.enable("png")
```

The default option is `alt.renderers.enable("html")`. For issues with rendering, consult [this section of the documentation](https://altair-viz.github.io/user_guide/display_frontends.html#troubleshooting). See also [this thread](https://stackoverflow.com/questions/71346406/why-are-my-altair-data-visualizations-not-showing-up-in-github) from one of the library maintainers on why Altair plots aren’t automatically rendered in GitHub or GitLab.

## Adjust Altair plot sizes

The default plot sizes are quite small. This isn’t an issue when they are rendered using JavaScript, but PNG versions of the plots might be a little too small to be clearly understood.

Use the `.properties()` method and `width` and `height` arguments (both take integer values as input) to adjust a plot’s size as desired.