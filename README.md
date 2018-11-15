# prospector pylint absolute import

This repo demonstrates an issue of prospector with pylint related to relative/absolute imports.

Use case: Your package wants to import another package `tzlocal` and also contains a file `tzlocal.py`.

## Installation
```bash
pip install -r requirements.txt
```

## Problem

### python2.7

```bash
pip install prospector==0.12.11  # installs pylint 1.9.3
```

```bash
pylint pkg/file1.py      # imports tzlocal package and does not complain
prospector pkg/file1.py  # imports tzlocal.py module and complains
```

Note:
```bash
python pkg/file1.py     # will use tzlocal.py module and fail

cd pkg
python file1.py         # will use tzlocal.py module and fail
pylint file1.py         # imports tzlocal.py module and complains
```

### python3.6

```bash
pip install prospector==1.1.3  # installs pylint 2.1.1
```

```bash
pylint pkg/file1.py      # imports tzlocal.py module and complains
prospector pkg/file1.py  # imports tzlocal.py module and complains
```

## Conclusion

While `pylint` was more forgiving than `prospector` under python2, the behavior of `pylint` and `prospector` is the same on python3.
