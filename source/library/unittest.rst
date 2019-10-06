
Unittest
========

The Python standard library has the :mod:`unittest` modules
containing tools for constructing and running tests.

Test cases
**********

Within this module the basic unit of testing
is the :class:`~unittest.TestCase`.
Using this class for your tests provides several
`assert methods <https://docs.python.org/3/library/unittest.html#assert-methods>`_
for your tests.

.. important:: Method names need to start with ``test``
   in order to be identified as actual tests.

E.g.::


    import unittest

    class MyTest(unittest.TestCase):
        def test_upper(self):
            self.assertEqual('foo'.upper(), 'FOO')

Running
*******

There are different ways to run the tests:

1. If you add::

    if __name__ == '__main__':
        unittest.main()

   the test case can be run from the command line
   as :command:`python test_mod.py`.
   Use the ``-v`` flag to have a more verbose output
   (:command:`python test_mod.py -v`).

2. Using the command :command:`python -m unittest`
   With this command you can:

   - we can specify a particular test (or group of tests, modules...) to be run,
     e.g. :command:`python -m unittest test_mod.MyTest.test_upper`
   - we can let python to find all the test itself
     using :command:`python -m unittest`.

     .. warning:: The discovery utility has some restrictions:
        modules should be importable from the top level directory
        of the project, by default test modules should be named as
        ``test*``... Read more in https://docs.python.org/3/library/unittest.html#test-discovery


Fixtures
********

The :mod:`unittest` module also include support for **test fixtures**.
They represent the preparation needed to perform one or more tests,
and any associate cleanup actions.
These fixtures are achieved with *setUp* and *tearDown* functions or methods.

:func:`~unittest.setUpModule` and :func:`~unittest.tearDownModule`
are called before any test and called once all test in the module are done.
:meth:`~unittest.TestCase.setUpClass` and :meth:`~unittest.TestCase.tearDownClass`
are called when the test case is created and destroyed
and :meth:`~unittest.TestCase.setUp` and :meth:`~unittest.TestCase.tearDown`
are called before and after each test in the test case.

E.g.::

    import unittest

    class MyTest(unittest.TestCase):

        def setUp(self):
            print('Before test')

        def tearDown(self):
            print('After test')

        def test_upper(self):
            print('During')
            self.assertEqual('foo'.upper(), 'FOO')


    if __name__ == '__main__':
        unittest.main()


Test suites
***********

In addition to *test cases*, the :mod:`unittest` module allows to
create **test suites** (collections of test cases).
In fact, using :func:`unittest.main` does create a *test suite*
with all test cases in the module.

Below there is an example of a *test suite* and a **test runner**
to execute it::

    suite = unittest.TestSuite()
    suite.addTest(MyTest())

    if __name__ == '__main__':
        runner = unittest.TextTestRunner()
        runner.run(suite)

