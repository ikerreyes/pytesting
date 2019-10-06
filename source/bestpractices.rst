
Best practices
==============

Some general rules of testing:

- A testing unit should focus on one tiny bit
  of functionality and prove it correct.
- Each test unit must be fully independent.
  Each test must be able to run alone.
- Try hard to make tests that run fast, so that is not painful to run the tests.
- Run the full test suite before a coding session, and run it again after.
- Use long and descriptive names for testing functions and document them.
- Keep your testing code up-to-date as with your code and docs.
- Do not focus only on positive testing, but also on negative.
  Check that the code breaks under the scenarios it should break.
- Keep your test separated from your source code in a **test**
  or **tests** folder.



----

Sources:
- https://docs.python-guide.org/writing/tests/