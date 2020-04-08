# exist-test-expath-skiptriggers

An app to prove the behavior of the repo.xml/skip-triggers element for the
test suite.

Modelled after https://github.com/dizzzz/existdb-trigger-test.

This app contains a data collection "testdata" which contains a single
test.xml file.

It also contains a collection.xconf file that defines an XQueryTrigger that
calls a logging XQuery (modules/trigger.xql) based on the example in
https://exist-db.org/exist/apps/doc/triggers

And it contains a repo.xml file with a "skip-triggers" element as suggested
in eXist-db PR #3338.

Behavior of this app:

In the normal case (triggers are enabled; no "skip-triggers" element in
repo.xml), the logging trigger is fired on installation of the test data and
thus the logfile "/db/triggers-log.xml" contains trigger log entries for the
collection "testdata" and the "test.xml" file.

In the special case that this apps should prove (triggers disabled because
element "skip-triggers" present in repo.xml), the test data gets installed,
but triggers do not fire, thus no log entries in file "/db/triggers-log.xml".
