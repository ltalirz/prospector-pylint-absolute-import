# prospector pylint absolute import

This repo demonstrates an issue of prospector with pylint related to relative/absolute imports.

Use case: Your package wants to import another package `tzlocal` and also contains a file `tzlocal.py`.

## Problem

### python2.7

```bash
pip install tzlocal
pip install prospector==0.12.11  # installs pylint 1.9.3
```

```bash
pylint pkg/file1.py      # imports tzlocal package and does not complain
prospector pkg/file1.py  # imports tzlocal.py module and complains
```

Note:
```bash
python pkg/file1.py     # uses tzlocal.py module and fails

cd pkg
python file1.py         # uses tzlocal.py module and fails
pylint file1.py         # imports tzlocal.py module and complains
```

### python3.6

```bash
pip install tzlocal
pip install prospector==0.12.11  # installs pylint 1.9.3

# Note: same behavior with more recent version:
pip install prospector==1.1.3  # installs pylint 2.1.1
```

```bash
pylint pkg/file1.py      # imports tzlocal package and does not complain
prospector pkg/file1.py  # imports tzlocal.py module and complains
```

## Conclusion

`pylint` is more forgiving than `prospector`.
