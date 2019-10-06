
Testing in Python
=================

The Python standard library contains modules to help
test automation. In addition, there are some
useful 3rd party libraries.

In most cases, the test execute a piece of code and
then you assert if certain condition is met.


Some libraries for testing in Python are:

.. toctree::
   :maxdepth: 2
   :caption: Contents:

   library/unittest
   library/doctest
   library/pytest


Other libraries are:

- :mod:`unittest.mock`: library that allows you to replace parts of your system
  under test with mock objects and make assertions about how they have been used.
- `Hypothesis <https://hypothesis.readthedocs.io/en/latest/>`_
- `Tox <https://tox.readthedocs.io/en/latest/>`_

----

Sources:
- https://docs.python-guide.org/writing/tests/
- https://docs.python.org/3/library/unittest.html
- https://docs.python.org/3/library/doctest.html
- https://docs.python.org/3/library/unittest.mock.html
