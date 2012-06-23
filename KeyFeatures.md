Key features
============

3D-engine
---------

3D-engine should be a full-blown framework for handling the data model
associated to the scene that is to be rendered. Also a compositor framework is
to be implemented, which allows creation of multi-threaded pipeline for
rendering. Scene system, pipeline and materials should be extendable. Also
custom object types should be supported.

3D-engine should also contain Hardware Abstraction Layer to abstract away
low-level graphics APIs (such as OpenGL and Direct3D).

Audio
-----

Probably only minimalistic audio library in early versions.

Input and event handling
------------------------

Input handling could also be quite minimalistic in early versions.


Cross-platform support
----------------------

Library should be supporting at least Windows, Linux, Mac OS X, Android, iOS and
Tizen platforms. Windows could support Direct3D and OpenGL in HAL. Other
platforms should be supported by OpenGL 3/4 and OpenGL ES (which is a subset of
OpenGL 3).

Audio could be supported on most platforms using OpenAL (Windows, Linux, 
Mac OS X, iOS, Tizen) and OpenSLES (Android).

Window and context creation could be done using GLFW and GLEW libraries on
Windows, Linux and Mac OS X. Platform-specific code is required for other
platforms.
