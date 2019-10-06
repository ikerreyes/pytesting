
py.test
=======

.. |pt| replace:: **py.test**
.. |ut| replace:: :mod:`unittest`

`py.test <https://docs.pytest.org/en/latest/contents.html>`_ is a simple and
powerful testing framework.
Is simple because it can be seen as a no-boilerplate alternative
to Python’s standard unittest module and powerful because
it is a fully-featured and extensible test tool.


Building a test with |pt| can be as simple as writing a function
with an assertion. E.g.::


    def test_upper():
        assert 'foo'.upper() == 'FOO'


One of the advantages of |pt| is that it is compatible with |ut|,
so you can use |ut| inside your scripts and run them with |pt|.

Running
*******

|pt| tests can be run in different ways:

1. Calling |pt| with the test module(s)
   (e.g. :command:`pytest test_mod.py`)

2. Using the `test discovery utility <https://docs.pytest.org/en/latest/goodpractices.html#conventions-for-python-test-discovery>`_:
   (:command:`pytest`).
   In short, it searches recursively starting from the current directory
   searching for ``test_*.py`` and ``*_test.py`` files and then
   collects all ``test_`` prefixed functions and methods inside ``Test``
   prefixed classes.

   .. tip:: Take a look at https://docs.pytest.org/en/latest/goodpractices.html#choosing-a-test-layout-import-rules
      to check how to structure your tests.

3. Similarly to |ut| and :mod:`doctest` you can use :command:`python -m pytest`


Fixtures
********

|pt| comes with a `fixture mechanism <https://docs.pytest.org/en/latest/fixture.html>`_
more powerful than the one of |ut|.



Set-up - tear-down
------------------

|pt| includes a similar `set up - tear down mechanism <https://docs.pytest.org/en/latest/xunit_setup.html>`_
to the one of |ut|.


Temporary directory
-------------------

|pt| ``tmpdir`` fixture creates a temporary directory as a
:class:`py.path.local` object you can use.
If you are not familiar with these objects, you can use :mod:`os.path`
methods::

    from os import path

    def test_tmp(tmpdir):
        assert path.exists(tmpdir)

By default, the temporary directory is created as ``pytest-NUM``,
and ``NUM`` is incremented on each run. The tmp directory exists
after the test, and entries older than 3 are automatically removed.


Logs
----

With |pt| is possible to capture the logs and test that
the right messages are send. The *caplog* fixture
is the one used for this purpose.
E.g.::

    import logging

    def f():
        # Remember that by default info messages will not be logged, only warning and above
        logging.info('Info')
        logging.warning('Warn')

    def test_logs(caplog):
        f()
        assert len(caplog.records) == 1
        for record in caplog.records:
            assert record.levelname == 'WARNING'
            assert 'wally' not in caplog.text


Parametrization
---------------

Using the parametrization capabilities of |pt|
we can test our function against multiple input arguments
easily. E.g.::

    import pytest

    @pytest.mark.parametrize("x", [0, 1])
    @pytest.mark.parametrize("y", [2, 3])
    def test_foo(x, y):
        pass

This way we can set up many combination of input parameters.
In addition, we can also use this utility to pass the
expected output. E.g.::

    import pytest

    def square(x):
        return x**2

    @pytest.mark.parametrize("x,result", [(0, 0), (1, 1), (2, 4), (3, 9)])
    def test_square(x, result):
        assert square(x) == result

Note that when you run this test the test will be passed 4 times,
one for each input::

    ============================= test session starts ==============================
    platform linux -- Python 3.6.6, pytest-3.10.0, py-1.7.0, pluggy-0.8.0
    rootdir: /home/user/testing, inifile:
    collected 4 items

    test_param.py ....                                                       [100%]

    =========================== 4 passed in 0.02 seconds ===========================


