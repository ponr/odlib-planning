ODSL
====

This file contains description for ODSL (OD Shading Language).

Motivation
==========

Main purpose for defining own shading language for ODlib-project is both to
increase portability and expressibility of shader code, and reducing the need
to write different shaders for different platforms.

Paradigm
========

ODSL is deisgned around concepts of functional programming languages. Shader 
can actually be considered as a mathematical function that takes certain inputs
and gives outputs. For example a vertex shader is merely a mathematical
function that is applied per vertex.

Implementation
==============

ODSL parser in ODlib will be implemented using Boost.Spirit parser framework
which generates recursive descent parser (LL(inf)-parser). Grammar is written
in inline C++ using PEG (Parsing Expression Grmmar) which is derivative of
EBNF.

Compatibility modes / Profiles
==============================

At some point. Compatibility modes for output languages should be considered.
It might not be possible to compile shader into different target languages
in some cases, since constraints of shading languages differ. It might be
good idea to design some kinds of profiles for different target platforms.

Types
=====

Types should be compatible with native types of target shading languages.

bool
int
float
Vector2, Vector3, Vector4
BVector2, BVector3, BVector4
Matrix2, Matrix3, Matrix4
Texture2D

Type Qualifiers
===============

uniform
-------

Value that does not change while processing the same primitive. Input parameter
which stays same for every shader instance.

attribute
---------

Value that changes per vertex. There can be multiple attributes per vertex.

varying
-------

Value that is written per vertex in vertex shader and gets interpolated per
fragment in fragment shader.

Operators
=========

[]
()
.

* /
+ -
< > <= =>
== !=
&&
^^
||

=
+= -=
*= /=

,

Example shader code
===================

Vertex shader
-------------

    uniform Matrix4 mvp_matrix;
    uniform Matrix3 normal_matrix;
    uniform Vector3 light_dir;

    attribute Vertex3 a_vertex;
    attribute Vertex3 a_normal;
    attribute Vertex2 a_texcoord;

    varying float v_diffuse;
    varying Vector2 v_texcoord;

    Vector3 ec_normal = normalize(normal_matrix * a_normal);
    v_diffuse = max(dot(light_dir, ec_normal), 0.0);
    v_texcoord = a_texcoord;
    od_position = mvp_matrix * a_vertex;

Tessellation control shader
---------------------------

TODO

Tessellation evaluation shader
------------------------------

TODO

Geometry shader
---------------

TODO

Fragment shader
---------------

TODO

Compute shader
--------------

TODO

Lexical analysis and atoms
==========================

See odlib.git/src/od/graphics/odsl/Lexer.hpp

BNF (LL(inf)-parser compatible grammar)
=======================================

See odlib.git/src/od/graphics/odsl/Grammar.hpp

