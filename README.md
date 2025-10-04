# Research Project Template (with uv)

This project template is inspired by the principles outlined by Patrick Minault in [The Good Research Code Handbook](https://goodresearch.dev) and uses the `uv` tool for a fast, modern, and reproducible Python workflow.

### First-Time Setup

1.  **Clone the repository:**
    ```bash
    git clone <your-repo-url>
    cd <your-repo>
    ```

2.  **Install `uv`:**
    Follow the instructions at [astral.sh/uv/install](https://docs.astral.sh/uv/getting-started/installation).

3.  **Create the virtual environment:**
    ```bash
    uv venv
    ```

4.  **Sync the environment:**
    This installs all the dependencies listed in `pyproject.toml` based on the versions in `uv.lock`.
    ```bash
    uv sync
    ```

You're all set! Your environment is now perfectly replicated.

---

### The Daily Workflow

Environment management becomes simple and robust.

1.  **Need a new package?** Add its name (e.g., `"seaborn"`) to the `dependencies` list in `pyproject.toml`.

2.  **Update your environment:** Run `uv sync`. This will update your `uv.lock` file and install the new package.

3.  **Run your code:** Execute scripts using `uv run`. This ensures your code runs inside the project's virtual environment.
    ```bash
    uv run python src/my_script.py
    ```

4.  **Work in Jupyter?** Add `ipykernel` to your `pyproject.toml`, run `uv sync`, and then install the kernel:
    ```bash
    uv run ipython kernel install --user --env VIRTUAL_ENV $(pwd)/.venv --name="my-research-project""
    ```
    You can now select the "my-research-project" kernel in Jupyter.

This declarative workflow guarantees that your environment is always in sync with your `pyproject.toml` and `uv.lock` files, eliminating environment drift and ensuring reproducibility.

---

### Additional Notes

- **Activating the environment:** If you prefer to activate the environment to work in an interactive shell (like with conda), run `source .venv/bin/activate` on macOS/Linux or `.venv\Scripts\activate` on Windows.

- **Updating packages:** To update all packages to the latest allowed versions, run `uv lock --upgrade` then `uv sync`. To upgrade a single package, run `uv pip install --upgrade <package-name>`.

- **Adding a GitHub repo as a dependency:** You can add a repository directly in your `pyproject.toml`:
    ```toml
    # pyproject.toml
    dependencies = [
        # Public repo
        "sphinx @ git+https://github.com/sphinx-doc/sphinx#egg=sphinx",
        # Private repo (requires SSH keys with GitHub)
        "my_pkg_name @ git+ssh://git@github.com/my-github-name/my_repo.git"
    ]
    ```
    To update a Git dependency to the latest commit, run `uv pip install --upgrade <package-name>`.

- **Editable installs for local development:** To work on a local package in development mode, you can install it as editable by using `uv pip install -e .` in the package directory. Note that this is imperitive and will be overwritten by `uv sync`, so it is not recommended.



