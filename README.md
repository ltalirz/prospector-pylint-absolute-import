# prospector pylint absolute import

This repo demonstrates an issue of prospector with pylint

## Installation
```bash
pip install -r requirements.txt
```

## Problem

### python2

 * python 2.7
 * pylint 1.9.3
 * prospector 0.12.11

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

### python3

 * python 3.6
 * pylint 2.1.1
 * prospector .1.1.3

```bash
pylint pkg/file1.py      # imports tzlocal.py module and complains
prospector pkg/file1.py  # imports tzlocal.py module and complains
```

## Conclusion

While `pylint` was more forgiving than `prospector` under python2, the behavior of `pylint` and `prospector` is the same on python3.
