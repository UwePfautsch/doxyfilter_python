# doxyfilter_python
Doxygen input filter for python

This script improves the use of Doxygen for programs written in Python.

## Install and Configuration

Install ``python`` on your computer and specify in your ``Doxyfile``:

````
EXTENSION_MAPPING      =
FILE_PATTERNS          = *.py \
                         *.pyw
INPUT_FILTER           = doxyfilter_python.py
````

## Improvements

The following improvements to ``doxygen v1.8.14`` are possible:
- Function definition may contain ``Type Hints`` 
  _(this aspect may be resolved in [doxygen issue 6462](https://github.com/doxygen/doxygen/issues/6462))_;
- Python ``docstrings`` are converted to the normal ``doxygen`` format;
- Type annotations are represented in doxygen format (from ``type hints`` or ``docstring`` types);
