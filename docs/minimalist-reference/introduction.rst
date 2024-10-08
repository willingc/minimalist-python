
.. _introduction:

************
Introduction
************

This reference manual describes the Python programming language.


.. _implementations:

Implementations
===============

Known implementations include:

CPython
   This is the original and most-maintained implementation of Python, written in C.

Jython
   Python implemented in Java. `the Jython website <https://www.jython.org/>`_.

Python for .NET
   This implementation actually uses the CPython implementation, but is a managed
   .NET application and makes .NET libraries available. `Python for .NET home page <https://pythonnet.github.io/>`_.

IronPython
   An alternate Python for .NET. `the IronPython website <https://ironpython.net/>`_.

PyPy
   An implementation of Python written completely in Python. `the PyPy project's home page <https://www.pypy.org/>`_.



.. _notation:

Notation
========

.. index:: BNF, grammar, syntax, notation

The descriptions of lexical analysis and syntax use a modified
`Backus–Naur form (BNF) <https://en.wikipedia.org/wiki/Backus%E2%80%93Naur_form>`_ grammar
notation.  This uses the following style of definition:

.. productionlist:: notation
   name: `lc_letter` (`lc_letter` | "_")*
   lc_letter: "a"..."z"

The first line says that a ``name`` is an ``lc_letter`` followed by a sequence
of zero or more ``lc_letter``\ s and underscores.  An ``lc_letter`` in turn is
any of the single characters ``'a'`` through ``'z'``.  (This rule is actually
adhered to for the names defined in lexical and grammar rules in this document.)

Each rule:
* begins with a name (which is the name defined by the rule) and ``::=``  
* vertical bar (``|``) is used to separate alternatives; it is the least binding operator in this notation.  
* star (``*``) means zero or more repetitions of the preceding item
* plus (``+``) means one or more repetitions
* a phrase enclosed in square brackets (``[ ]``) means zero or one occurrences (in other words, the enclosed phrase is optional).  
* ``*`` and ``+`` operators bind as tightly as possible; parentheses are used for grouping.  
* Literal strings are enclosed in quotes.
* White space is only meaningful to separate tokens. 

Rules are normally contained on a single line; rules with many alternatives may be formatted alternatively with each line after
the first beginning with a vertical bar.

.. index:: lexical definitions, ASCII

In lexical definitions (as the example above), two more conventions are used:

* Two literal characters separated by three dots mean a choice of any single character in the given (inclusive) range of ASCII characters
* A phrase between angular brackets (``<...>``) gives an informal description of the symbol defined; e.g., this could be used to describe the notion of 'control character' if needed.

Even though the notation used is almost the same, there is a big difference
between the meaning of lexical and syntactic definitions: 
* a lexical definition operates on the individual characters of the input source,
* a syntax definition operates on the stream of tokens generated by the lexical analysis.

All uses of BNF in the next chapter ("Lexical Analysis") are lexical
definitions; uses in subsequent chapters are syntactic definitions.

