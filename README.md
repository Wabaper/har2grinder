har2grinder
===========

Creates test files for The Grinder based on HTTP Archive (HAR) files generated by Chrome DevTools.

Overview
--------

The har2grinder script creates a test file, which can be run by [The Grinder][grinder] load testing framework.

The test files are generated from [HTTP Archive (HAR) files][har], which can be generated using Chrome DevTools.


Recording a test using Chrome DevTools
--------------------------------------

1. Fire up Chrome and open the DevTools.

2. Open the Network tab of the DevTools.

4. Clear the Network history ("no entry" icon).

5. Choose the option to `Preserve log` upon navigation.

5. Choose the option to `Disable cache`.

6. Navigate around your site.

7. After you navigate to the pages you want to test, right-click on the network history panel and choose "Copy > Copy All as HAR". Save the clipboard to a .har file.

For more information check out [my blog post][blog].

Converting a HAR file to a Grinder test
---------------------------------------

To convert the recorded navigation to a Grinder test, run the `har2grinder` script:

    python har2grinder.py my_website_test.har > my_website_grinder_test.py


Settings
--------

You can specify options by creating a file named `settings.py` in the directory which holds the `har2grinder` script.

Currently supported options:

* `SLEEP_BETWEEN_PAGES` - the time which Grinder will wait after loading the first page before proceeding to the next [milliseconds].
* `EXCLUDED_DOMAINS` - a tuple, which list domains for files hosted by external CDNs, which are not part of your test.


Known limitations
-----------------

* no support for websockets

[grinder]: http://grinder.sourceforge.net  "The Grinder, a Java Load Testing Framework"
[har]: https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/HAR/Overview.html "HTTP Archive (HAR) format"
[blog]: http://michal.karzynski.pl/blog/2013/09/28/website-performance-script-for-the-grinder-using-har2grinder/ "Recording a website performance test for The Grinder using Chrome DevTools"