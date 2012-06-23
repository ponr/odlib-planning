Library Design issues
=====================

* Language to be used is C++. In particular, C++11 which is the newest
  extension to the C++ language.

* Aim for exceptionless design of library. Exceptions work badly on some 
  platforms and may grow code size significantly. Instead error codes
  and predefined functionality is emphasized.

* Use of only single inheritance. Multiple inheritance adds unnecessary
  complexity to the library.
