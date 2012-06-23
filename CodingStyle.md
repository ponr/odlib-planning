Coding Style
============

Code files
----------

* Programming language is English, which means everything included in code
  files should be in English (comments, code, etc.)

* Files containing implementation code have extension .cpp and headers have
  .hpp extensions. Includable implementation files should have extension .icc
  (used with template classes).

Header files (.hpp)
-------------------

* One header file should specify only one unit of code (class or namespace).

* Doxygen-comments should to be written at least on public parts of the class.
  Comment should contain brief introduction about class/function/structure
  functionality and purpose.

* Header file can be considered properly documented/commented if test cases can
  be constructed and class can be used.

* Header file should only contain specifications, unless it contains
  inline functions or template classes. Template class implementation code
  should be inserted into its own file (extension .icc) and included from
  appropriate spot in header file.

* Headers should not contain using-declarations.

* Headers should only contain #include-declarations necessary for the header
  file.

* If only a pointer or reference to class is used in header, predeclaration
  should be used. However, only ODlib internal classes should be predeclared.

* Header file should be protected from multiple inclusion using preprocessor
  macros. Macro is to be named based on namespace and class, such as
  OD_GFX_MODEL_HPP for class Model in namespace od::gfx.

Implementation files (.cpp)
---------------------------

* Implementation files should only contain header files crucial for
  implementation.

* ODlib-specific header files should be included before external libraries.

* Function implementations should be in same order than in header.

Naming conventions
------------------

* All code should be written to namespace specific to module of the library.

* Names beginning with underscore (_) or containing double underscore (__)
  are forbidden.

* Namespaces are named with lowercase.

* Classes are named with CamelCase convention.

* Functions are named with first letter lowercase camelCase.

* Contants are named with CAPITAL letters.

Variables and Contants
----------------------

* Scope must be as small as possible. No global variables or singleton pattern
  are used in this library.

* Every variable must be initialized. Class default constructor is sufficient
  initialization if exists.

* Every variable must be declared separately.

* Use of macros (#define) is forbidden. Use inline functions instead.

* #define must not be used to define constants.

* Variables must be cast with specific type-casting operator.
  (static_cast, dynamic_cast, reinterpret_cast).

* Use of const_cast is forbidden.

* When declaring constants, const-operator should be placed after
  the type of the variable.

* ODlib declares set of integer types, which must be used in the internal
  implementation.

  Integer types: OD[u]int[8,16,32,64]

* When using external libraries, library-specific types should be used.
  Such as: GLfloat, png_voidp.

