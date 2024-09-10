====================================
Minimalist: Python Developer's Guide
====================================

.. raw:: html

    <script>
    document.addEventListener('DOMContentLoaded', function() {
      activateTab(getOS());
    });
    </script>

.. highlight:: bash

This guide is a comprehensive resource for :ref:`contributing <contributing>`
to Python_

.. _quick-reference:

Quick reference
---------------

Here are the basic steps needed to get set up and contribute a patch.
For complete
instructions please see the :ref:`setup guide <setup>`.

1. Install and set up :ref:`Git <vcsetup>` and other dependencies
   (see the :ref:`Git Setup <setup>` page for detailed information).

2. Fork `the CPython repository <https://github.com/python/cpython>`_
   to your GitHub account and :ref:`get the source code <checkout>` using::

      git clone https://github.com/<your_username>/cpython
      cd cpython

3. Build Python:

   .. tab:: Unix

      .. code-block:: shell

         ./configure --with-pydebug && make -j

   .. tab:: macOS

      .. code-block:: shell

         ./configure --with-pydebug && make -j

   .. tab:: Windows

      .. code-block:: dosbatch

         PCbuild\build.bat -e -d

   See also :ref:`more detailed instructions <compiling>`,
   :ref:`how to install and build dependencies <build-dependencies>`,
   and the platform-specific pages for :ref:`Unix <unix-compiling>`,
   :ref:`macOS <macOS>`, and :ref:`Windows <windows-compiling>`.

4. :ref:`Run the tests <runtests>`:

   .. tab:: Unix

      .. code-block:: shell

         ./python -m test -j3

   .. tab:: macOS

      .. code-block:: shell

         ./python.exe -m test -j3

      Note: :ref:`Most <mac-python.exe>` macOS systems use
      :file:`./python.exe` in order to avoid filename conflicts with
      the ``Python`` directory.

   .. tab:: Windows

      .. code-block:: dosbatch

         .\python.bat -m test -j3

5. Create a new branch where your work for the issue will go, for example::

      git checkout -b fix-issue-12345 main

   If an issue does not already exist, please `create it
   <https://github.com/python/cpython/issues>`_.  Trivial issues (for example, typo fixes) do
   not require any issue to be created.

6. Once you fixed the issue, run the tests, and the patchcheck:

   .. tab:: Unix

      .. code-block:: shell

         make patchcheck

   .. tab:: macOS

      .. code-block:: shell

         make patchcheck

   .. tab:: Windows

      .. code-block:: dosbatch

         .\python.bat Tools\patchcheck\patchcheck.py

   If everything is ok, commit.

7. Push the branch on your fork on GitHub and :ref:`create a pull request
   <pullrequest>`.  Include the issue number using ``gh-NNNN`` in the
   pull request description.  For example:

   .. code-block:: text

      gh-12345: Fix some bug in spam module

8. Add a News entry into the ``Misc/NEWS.d`` directory as individual file. The
   news entry can be created by using `blurb-it <https://blurb-it.herokuapp.com/>`_,
   or the :pypi:`blurb` tool and its ``blurb add``
   command. Please read more about ``blurb`` in its
   `repository <https://github.com/python/blurb>`_.

.. note::

   First time contributors will need to sign the Contributor Licensing
   Agreement (CLA) as described in the :ref:`Licensing <cla>` section of
   this guide.

Proposing changes to Python itself
----------------------------------

Improving Python's code, documentation and tests are ongoing tasks that are
never going to be "finished", as Python operates as part of an ever-evolving
system of technology.  An even more challenging ongoing task than these
necessary maintenance activities is finding ways to make Python, in the form of
the standard library and the language definition, an even better tool in a
developer's toolkit.

While these kinds of change are much rarer than those described above, they do
happen and that process is also described as part of this guide:

* :ref:`stdlibchanges`
* :ref:`langchanges`

Key resources
-------------

* Coding style guides

  * :PEP:`7` (Style Guide for C Code)
  * :PEP:`8` (Style Guide for Python Code)

* `Issue tracker`_

  * :ref:`experts`

* `Buildbot status`_
* Source code

  * `Browse online <https://github.com/python/cpython/>`_
  * `Snapshot of the *main* branch <https://github.com/python/cpython/archive/main.zip>`_

* PEPs_ (Python Enhancement Proposals)
* :ref:`help`
* :ref:`developers`


.. _resources:

Additional resources
--------------------

* Anyone can clone the sources for this guide.  See :ref:`devguide`.
* Help with ...

  * :ref:`exploring`
  * :ref:`grammar`
  * :ref:`parser`
  * :ref:`compiler`
  * :ref:`garbage_collector`

* Tool support

  * :ref:`gdb`
  * :ref:`clang`
  * Various tools with configuration files as found in the `Misc directory`_
  * Information about editors and their configurations can be found in the
    `wiki <https://wiki.python.org/moin/PythonEditors>`_

* `python.org maintenance`_
* :ref:`Search this guide <search>`

.. _contents:

Full table of contents
----------------------

.. toctree::
   :maxdepth: 3

   getting-started/index
   developer-workflow/index
   triage/index
   documentation/index
   testing/index
   development-tools/index
   core-developers/index
   internals/index
   versions

.. _Buildbot status: https://www.python.org/dev/buildbot/
.. _Misc directory: https://github.com/python/cpython/tree/main/Misc
.. _PEPs: https://peps.python.org/
.. _python.org maintenance: https://pythondotorg.readthedocs.io/
.. _Python: https://www.python.org/
.. _Core Python Mentorship: https://www.python.org/dev/core-mentorship/
.. _PyPy: https://pypy.org
.. _Jython: https://www.jython.org/
.. _IronPython: https://ironpython.net/
.. _Stackless: https://github.com/stackless-dev/stackless/wiki/
.. _MicroPython: https://micropython.org/
.. _CircuitPython: https://circuitpython.org/
.. _Issue tracker: https://github.com/python/cpython/issues
