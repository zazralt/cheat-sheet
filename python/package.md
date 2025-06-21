# Python Package

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
