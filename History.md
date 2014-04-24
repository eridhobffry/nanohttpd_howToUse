## Nanohttp.com site

* http://nanohttpd.com - went live July 1st, 2013.
* Moved hosting, adding news and better documentation April 2014.

## Version History (Java 6+ version)
* 2.1.0 (2014-04-23) : Websocket Support
* 2.0.5 (2013-12-12) : Cleanup and stability fixes.
* 2.0.4 (2013-09-15) : Added basic cookie support, experimental SSL support and runtime extensions.
* 2.0.3 (2013-06-17) : Implemented 'Connection: keep-alive', (tested against latest Mozilla Firefox).
* 2.0.2 (2013-06-06) : Polish for the webserver, and fixed a bug causing stack-traces on Samsung Phones.
* 2.0.1 (2013-05-27) : Non-English UTF-8 decoding support for URLS/Filenames
* 2.0.0 (2013-05-21) : Released - announced on FreeCode.com
* (2013-05-20) : Test suite looks complete.
* (2013-05-05) : Web server pulled out of samples and promoted to top-level project
* (2013-03-09) : Work on test suite begins - the push for release 2.0.0 begins!
* (2013-01-04) : Initial commit on "uplift" fork

## Version History (Java 1.1 version)

* 1.27 (2013-04-01): Merged several bug fixes from github forks
* 1.26 (2013-03-27): fixed an off-by one bug
* 1.25 (2012-02-12): rudimetary PUT support, buffer size now configurable, support for etag "if-none-match" check, log output stream now configurable
* 1.24 (2011-08-04): etags + video mime types (for HTML5 video streaming)
* 1.23 (2011-08-02): better support for partial requests
* 1.22 (2011-07-21): support for custom www root dir
* 1.21 (2011-01-03): minor bug fixes
* 1.2  (2010-12-31): file upload (by Konstantinos Togias) and some small bug fixes
* 1.14 (2010-08-20): added a stop() function
* 1.13 (2010-06-27): fixed a wrong case in 'range' header
* 1.12 (2010-01-07): fixed a null ptr exception
* 1.11 (2008-04-21): fixed a double URI decoding (caused problems when there was a percent-coded percent)
* 1.10 (2007-02-09): improved browser compatibility by forcing headers lowercase; fixed a POST method over-read bug
* 1.05 (2006-03-30): honor Content-Length header; support for clients that leave TCP connection open; better MIME support for symlinked files
* 1.02 (2005-07-08): fixed a stream read starvation bug
* 1.01 (2003-04-03): first published version
