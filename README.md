# prospector pylint absolute import

This repo demonstrates an issue of prospector with pylint

## Installation
```
pip install -r requirements.txt
```

## Problem

```
pylint pkg/file1.py      # does not complain about 
prospector pkg/file1.py  # complains
```
