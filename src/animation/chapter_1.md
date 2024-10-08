# Linear Algebra and OpenGL Setup

This section wil be quite brief, the most important things to know from this
section is essentially how does the Render Pipeline work, what is an OpenGL and
of course the basic linear algebra operations we care about like matrix
multiplication, cross product, dot product and scalar multiplication.

## Vector Arithmetic

- Scalar multiplication $s \times{} <1, 2, 3> = <s, 2s, 3s>$
- Addition $<1, 2, 3> + <1, 2, 3> = <2, 4, 6>$
- Cross product and dot product, you can use dot product to find the angle between 2 vectors remember that if dot product is 0 then the vectors are perpendicular.

## Matrix Operations

- Matrix multiplication is not commutative and goes row by column hence rows in A multiply columns in B using the dot product to get the result at row col.

## OpenGL Render Pipeline

- Take in some vertex data, assemble the shape, geometry shader, tesselation shader, rasterization, fragment shader into test and blending
- All vertices and fragments can be thought of as independent
- VBO stands for Vertex Based Object
- VAO stands for Vertex Array Object
- Attribute Pointer points from VBO to some block inside of VAO

## Shaders

- How to draw something in a unique way typically there are 2 kinds of shader a vertex shader and a fragment shader
- Vertex shader handles processing of vertices
- Fragment shader handles fragments generated by rasterization
