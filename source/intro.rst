
Testing
=======

Testing (in software) is an investigation conducted to check the
quality. Testing is used for:

- **validation**: check if *requirements* are met.
  E.g. test if a task is completed within certain time limits.
- **verification**: find *errors* in the software.
  Errors are mistakes in the code so that the desired
  output and the actual one differ.
  Errors cause faults (a.k.a bugs) which lead to failures.
  E.g. test if a program responds correctly to different outputs.

.. important::

   Testing cannot establish that a product functions properly under all conditions,
   but only that it does not function properly under specific conditions.

Testing can be done **manually** (e.g. checking if a webpage opens),
but in most cases the use of **automated** tools is required.

Traditionally, two approaches can be distinguished in testing:

- the **black-box** testing: test the *functionality* of a program
  without worrying on the design and structure of the code.
  Typically, for a set of inputs and desired outputs, it is tested
  if the actual output corresponds to the desired one.
- the **white-box** testing: test the program and the *implementation*.
  This kind of tests can help to improve code efficiency and structure.

Recently, *grey-box* approaches have been introduced making the above
distinction slightly more blurred.

Testing can also be divided into **static testing**
(e.g. reviews, inspections) which involves *verification*,
and **dynamic testing** (executing code given a set of test cases)
which also involves validation.

Levels
------

Software can be validated at various levels:

Unit testing
************

Verify the functionality of a specific section of code
(e.g. a function or a class).
Usually, these tests are written by the developers
as they build the code (white-box approach).

Although unit testing does not verify a whole piece of code,
it gives information on its building blocks.

Integration testing
*******************

This type of testing aims to ensure that interfaces between components
work (e.g. arguments passing).

System testing
**************

The software is tested as a whole.

Acceptance testing
******************

Test user interaction and response (e.g. alpha and beta testing).

----

.. note:: Although in many cases testing is consider as something to a
   validation/verification tool while you are developing (or after you
   develop) your software it is not always the case.
   For example, :abbr:`TDD (Test Driven Development)` is a process in
   which requirements are turned into test cases and then the software
   is improved to pass the new tests.

----

Further reading in:

- https://www.tutorialspoint.com/software_engineering/software_testing_overview.htm
- https://en.wikipedia.org/wiki/Software_testing