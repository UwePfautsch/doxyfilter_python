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
- Function definition may contain ``type hints`` 
  _(this aspect may be resolved in [doxygen issue 6462](https://github.com/doxygen/doxygen/issues/6462))_;
- Python ``docstrings`` are converted to the normal ``doxygen format`` (cf. example 1);
- Type annotations from ``type hints`` (cf. example 2) or from ``docstring types`` (cf. example 3) are taken over to ``doxygen format``;

## Examples

### Example 1

````
def formattet_text():
    """ formatted text

    The following list consists of items and sub items:
    - aaa = 1st item
      - aaa.11 = 1st sub-item of item 'aaa'
      - aaa.22 = 2nd sub-item of item 'aaa'
    - bbb = 2nd item
      - bbb.11 = 1st sub-item of item 'bbb'
      - bbb.22 = 2nd sub-item of item 'bbb'
    """
    return
````

is converted to

````
##      formatted text
#
#     The following list consists of items and sub items:
#     - aaa = 1st item
#       - aaa.11 = 1st sub-item of item 'aaa'
#       - aaa.22 = 2nd sub-item of item 'aaa'
#     - bbb = 2nd item
#       - bbb.11 = 1st sub-item of item 'bbb'
#       - bbb.22 = 2nd sub-item of item 'bbb'
#
def formattet_text():
    return
````

### Example 2

````
def typehint(a: int, b: int) -> int:
    """ only type-hints are present

    :param a: left
    :param b: right
    :return: summary
    """
    return a + b
````

is converted to

````
##      only type-hints are present
#
# \param a (int) left
# \param b (int) right
# \return (int) summary
#
def typehint(a, b): # type-hints removed
    return a + b
````

### Example 3

````
def docstring(a, b):
    """ only docstring-types are present

    :param a: left
    :type a: int
    :param b: right
    :type b: int
    :return: summary
    :rtype: int
    """
    return a + b
````

is converted to

````
##      only docstring-types are present
#
# \param a (int) left
# \param b (int) right
# \return (int) summary
#
def docstring(a, b):
    return a + b
````
