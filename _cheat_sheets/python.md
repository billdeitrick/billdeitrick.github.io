---
description: Commonly referenced tips, tricks and docs for the Python programming langauge.
---

# Links

* [Python Magic Methods and __getattr__](https://blog.rmotr.com/python-magic-methods-and-getattr-75cf896b3f88)
* [Python Magic Methods and Operator Overloading](https://www.python-course.eu/python3_magic_methods.php)

# How To's and Code Samples

## Python 3 Exceptions in Unit Tests

Python 3 introduces the ability to verify exceptions were raised in unit tests without having to introduce additional exception handling code. A context manager is utilized to provide this capability.

Example:
```python
...UNIT TEST CODE...

with self.assertRaises(ExceptionType):
    function_that_raises_exception()
    
...MORE UNIT TEST CODE...
```