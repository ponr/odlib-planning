ODSL
====

This file contains description for ODSL (OD Shading Language).

Motivation
==========
Main purpose for defining own shading language for ODlib-project is both to
increase portability and expressibility of shader code, and reducing the need
to write different shaders for different platforms.

Types
=====

void
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
Value that does not change while processing the same primitive. Kind of a
parameter for shader program.

attribute
---------
Value that changes per vertex.

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

input
{
    uniform Matrix4 mvp_matrix;
    uniform Matrix3 normal_matrix;
    uniform Vector3 light_dir;

    attribute Vertex3 a_vertex;
    attribute Vertex3 a_normal;
    attribute Vertex2 a_texcoord;
}

output
{
    od_position;

    varying float v_diffuse;
    varying Vector2 v_texcoord;
}

main()
{
    Vector3 ec_normal = normalize(normal_matrix * a_normal);
    v_diffuse = max(dot(light_dir, ec_normal), 0.0);
    v_texcoord = a_texcoord;
    od_position = mvp_matrix * a_vertex;
}

Fragment shader
---------------

input
{
}

output
{
}

main()
{
}

Lexical analysis
================

BNF
===
