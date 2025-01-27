# test-python

## Challenge
Enable customers to use existing repositories of Python automation scripts from within their Tines stories, with minimal updates needed to make it work

## What is needed to make it work?
Additional reading
* https://pip.pypa.io/en/stable/topics/vcs-support/
* https://www.geeksforgeeks.org/how-to-install-a-python-package-from-a-github-repository/

0. The repo containing the scripts needs to be a package, which means a `pyproject.toml` file or a `setup.py` file must exist in the root of the repo. You can run `uv init` to generate the project files for you, see docs [here](https://docs.astral.sh/uv/guides/projects/)
1. Use `uv`'s builtin "inline dependency" feature to declare scripts' dependencies in code blocks. See [/testing-github-deps.py](./testing-github-deps.py)
2. When listing the dependencies for the script, reference the Git repo. This is the example used in `/testing-github-deps.py`:
```
# /// script
# dependencies = [
#   "test_python@git+https://github.com/brady-spiva/test-python.git"
# ]
# ///
```
3. With the dependencies listed inline, we can run the command `uv run testing-github-deps.py` and then access and use the scripts locally