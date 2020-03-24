API: some general principles
============================

Input points
------------

All the functions of the library that compute a kernel matrix take one
or two "input points" arguments, denoted by ``X`` and (when there are
two of them) ``Y``.
Mathematically, an "input points" argument ``X`` represents an
:math:`n`-tuple :math:`\left( x_1, \ldots, x_n \right)` of points in
the input set :math:`\mathbb{X}`.
In the first stages of its development, libkmat will deal exclusively
with the following setting:

* :math:`\mathbb{X} \subset \mathbb{R}^d` for some :math:`d`;
* the coordinates :math:`x_{i,j}` of a point :math:`x_i \in
  \mathbb{X}` are represented by :math:`d` *double-precision*
  (``double``) floating point numbers;
* ``X`` is a ``double*`` pointer to an :math:`n \times d`
  double-precision matrix in *column-major* format.

Note that such an ``X`` can equivalently be interpreted as a :math:`d
\times n` double-precision matrix in *row-major* format.

In a more distant future, other settings should be considered for
wider applicability:

* the case where ``X`` is a ``double*`` pointer to an :math:`n \times
  d` double-precision matrix in *row-major* format (equivalently, a
  :math:`d \times n` double-precision matrix in *column-major* format);
* cases where the elements of ``X`` are not contiguous in memory:
  non-unit stride, matrix views, Ilife vectors, etc.;
* cases where :math:`\mathbb{X}` is no longer a subset of
  :math:`\mathbb{R}^d` (or at least can no longer conveniently be
  represented as such), for instance the set of all words constructed on
  a given finite alphabet.
