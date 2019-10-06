

Doctest
=======

:mod:`doctest` is another Python built-in module that searches
for pieces of text that look like interactive Python sessions,
and then executes those sessions to verify that they work exactly as shown.


A simple example::

    def square(x):
        """Return the square of x.

        >>> square(2)
        4
        >>> square(-2)
        4
        """

        return x * x



These tests can be run similar to the unittest commands:

1. Adding::

    if __name__ == '__main__':
        import doctest
        doctest.testmod()

   makes the doctest runnable using :command:`python mod.py -v`


2. The :command:`python -m doctest -v mod.py`

