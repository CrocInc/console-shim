console-shim
============

Description (forked)
-----------
It's a fork of https://github.com/kayahr/console-shim library.
The fork contains the following changes:
- conditional compilation (`@cc_on`) was replaced with `document.documentMode` check.
  Reason: `@_jscript_version` doesn't work in emulation mode, e.g. in IE11 we emulates IE8, so logging fails.
- applied PR https://github.com/kayahr/console-shim/pull/8 to remove possible memory leak in old IE
- removed "log4javascript" support
- added time/timeEnd wrapping (similar to log/debug/etc methods) for the case of IE8 emulation in newer IE (IE11)

Description (original)
-----------

This small shim implements or completes `window.console` on browsers which
have no or incomplete console support.  The goal is to be able to use the
console in JavaScript applications without having to worry about JavaScript
errors which might occur if a browser does not provide a native console or
has an incomplete console implementation. 


Implemented functions
---------------------

This section lists the actions done by this shim if a specific console
feature is not supported by the browser.

* **log**: Linked to log4javascript if possible. Otherwise a dummy function is
  installed to ignore logging completely.
* **debug**: Linked to log4javascript if possible or to the log method.
* **info**: Linked to log4javascript if possible or to the log method.
* **warn**: Linked to log4javascript if possible or to the log method.
* **error**: Linked to log4javascript if possible or to the log method.
* **assert**: Full implementation which logs an error message when the assert 
  expression is false.
* **clear**: Empty dummy function.
* **dir**: Linked to log message. Hopefully the browser or external logging
  facility knows how to dump objects.
* **dirxml**: Linked to log message. Hopefully the browser or external logging
  facility knows how to dump DOM nodes.
* **trace**: Empty dummy function.
* **group**: Empty dummy function.
* **groupCollapsed**: Empty dummy function.
* **groupEnd**: Empty dummy function.
* **time**: Full implementation which records the current time under the
  specified name.
* **timeEnd**: Full implementation which calculates the difference between
  the current time and the recorded start time and logs it.
* **timeStamp**: Empty dummy function.
* **profile**: Empty dummy function.
* **profileEnd**: Empty dummy function.
* **count**: Empty dummy function.
* **exception**: Linked to console.error. Not exactly the same but at least
  all parameters are logged as an error message then.
* **table**: Full implementation. Output is not really beautiful but it
  works.

License
-------

Copyright (c) 2011-2012 Klaus Reimer <k@ailis.de>

Permission is hereby granted, free of charge, to any person obtaining a
copy of this software and associated documentation files (the "Software"),
to deal in the Software without restriction, including without limitation
the rights to use, copy, modify, merge, publish, distribute, sublicense,
and/or sell copies of the Software, and to permit persons to whom the
Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING
FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER
DEALINGS IN THE SOFTWARE.


Reporting problems
------------------

If you have any problems with console-shim or find bugs in the
software then please create an
[issue](https://github.com/kayahr/console-shim/issues).
