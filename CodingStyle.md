Coding Style
============

This C++ style guide is mostly based on Tampere University of Technology,
Faculty of Computer Science C++ style guide (in finnish) and customized for
use in this project:
http://www.cs.tut.fi/~oliot/kirja/tyyliopas/

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

* Use of macros (\#define) is forbidden. Use inline functions instead.

* \#define must not be used to define constants.

* When declaring constants, const-operator should be placed after
  the type of the variable.

* ODlib declares set of integer types, which must be used in the internal
  implementation.

  Integer types: OD[u]int[8,16,32,64]

* When using external libraries, library-specific types should be used.
  Such as: GLfloat, png_voidp.

Typecasting
-----------

* No part of the program must rely on implicit typecasting.

* Variables must be cast with specific typecasting operator.
  (static_cast, dynamic_cast, reinterpret_cast).

* Use of const_cast is forbidden.

Whitespace
----------

* Maximum width of line is 79 characters. 

* if, else, while, for, do, switch, case -operators are always followed by
  code block.

* Braces ({, }) are placed on their own lines.

* Pointer and reference symbols ( *, &) do not have whitespace with type.
  Example: ODuint16* foo;

C-features in C++
-----------------

* Program must not be exited using exit() or abort().

* goto-operator is forbidden.

* Use C++ streams (cin, cout, cerr, clog) instead of C Standard IO (printf(),
  scanf(), sprintf(), ...)

* Functions malloc(), realloc() and free() are forbidden, because they do not
  handle construction and deconstruction of C++ classes.
  Exception: If highly optimized datastructures require usage of these,
             usage might be permitted for special cases.

* When including C-libraries, include-directives must be put inside
  extern "C" { } block.

Functions and member functions
------------------------------

* Function parameters must be same in declaration and implementation.

* When using an object as parameter, constant reference is preferred.

* Function must not have undefined parameter list.

* Function default parameters must be visible in declaration.

* Function return value must always be defined.

* Function must not return pointer to local variable.

* Member function should be declared constant whenever possible.

Classes and objects
-------------------

* Classes are implemented using C++ keyword class, and structures are
  implemented using keyword struct. (C++ class==struct)

* Structures can have constructor and destructor but no other functions.

* Class parts are introduced in this order: public, protected, private.

* Class member variables are always declared as private.

* There is never implementation code in class declaration.

* Classes should not have friends except in very specific situations.

Memory management
-----------------

* Freeing of dynamically allocated memory is responsibility of the class
  which allocated it (in most cases).

* Operator delete must only be used for freeing memory allocated with new.

* Operator delete[] must only be used for freeing memory allocated with new[].

* If delete operator has a parameter of pointer variable, it is assigned with
  0 after deletion.

Object construction and destruction
-----------------------------------

* Dynamically created object destruction should be verified using
  smart pointers.

* Every class must have at least one constructor.

* Constructor or destructor must not call virtual functions.

* Constructor or destructor must not use global or static objects.

* One parameter constructor must be prefixed with explicit keyword.
  Except for copy constructor, which must not have this keyword.

* Base class destructor must be either public virtual or protected non-virtual.

* Destructor must free all resources used by object.

Object copying and assignment
--------------

* Every class must have declared copy constructor and assignment operator.
  Declaration should be in private part if it is not implemented.

* Inherited class copy constructor or assignment operator must call
  base class copy constructor or assignment operator.

* Assignment operator must be protected from "assigning itself". (a = a)

* Assignment operator returns *this.

Inheritance
-----------

* Only public-inheritance is permitted.

* Multiple inheritance is forbidden in this project.

* All member functions in interface class are pure virtuals.

* Inherited class constructor must call constructor of base class.

* Functions in inherited class should have virtual if those are derived from
  base class.

* Non-virtual member function must not be redefined in inherited class.

* Inherited virtual member function default parameter must not be redefined.

Templates
---------

* Template typename parameter requirements must be documented in
  declaration of the template.

Exceptions and errors
---------------------

* Exceptions are not used in this project. However you may find situations
  where you need to handle exceptions thrown by external libraries.

* No function in ODlib should throw exception or let exceptions leak.

* Class behaviour in errors should be predefined.
