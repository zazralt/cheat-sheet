# Python Package

Links: [github actions](https://docs.github.com/en/actions/use-cases-and-examples/building-and-testing/building-and-testing-python)

## Installing a package
```bash
pip install {package}
```

## Project structure
```
your-package-name/
├── .gitignore
├── LICENSE
├── README.md
├── pyproject.toml
├── your_package/
│   ├── __init__.py
│   └── your_module.py
```

## Create a package in github
1. Add your licence, e.g. MIT.
2. Add your readme.
3. Create the `pyproject.toml` file containing the metadata and build configuration.
4. Write your python code in the `src/` folder.
5. Edit `__init__.py` to expose your functions.
6. Add unit tests.
7. Push to github.


## Install package from github
```bash
pip install git+https://github.com/<username>/<repository>.git
```

## Import your package
```
from my_package import my_function
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
