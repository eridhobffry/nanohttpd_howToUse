The project is managed with a "fork and pull-request" pattern.

If you want to contribute, fork this repo and submit a pull-request of your changes when you're ready.

Anyone can create Issues, and pull requests should be tied back to an issue describing the purpose of the submitted code.

## The Tests

In an ideal world for a bug fix: write a test of your own that fails as a result of the bug being present.  Then fix the bug so that your unit-test passes.  The test will now be a guard against the bug ever coming back.

Similarly for enhancements, exercise your code with tests.

Whatever else happens, if you make changes to the code, the unit & integration test suite (under ```core/src/main/test/```) should all continue to function.  Pull requests with broken tests will be rejected.
