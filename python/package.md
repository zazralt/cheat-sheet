# Python Package

## Project structure
```
your-package-name/
├── .git/
├── .gitignore
├── LICENSE
├── README.md
├── pyproject.toml
├── src/
│   └── your_package/
│       ├── __init__.py
│       └── your_module.py
├── tests/
│   └── test_your_module.py
```

## Create a package in github
1. Create the `pyproject.toml` file containing the metadata and build configuration.
2. Write your python code in the `src/` folder.
3. Add unit tests.
4. Push to github.


## Install package from github
```bash

# To install a package:
pip install git+https://github.com/<username>/<repository>.git

# To install a specific branch:
pip install git+https://github.com/<username>/<repository>.git@<branch>

# To install a specific commit:
pip install git+https://github.com/<username>/<repository>.git@<commit_hash>

```

## Import package from local file
```python
import sys
sys.path.append('/path/to/cloned/repo')

from mypackage import mymodule

```

## Import dependency
Add to requirements.txt:
```
git+https://github.com/<username>/<repository>.git@main
```

## Publishing on PyPI

```bash
python -m build
twine upload dist/*
```
