Scala
=====

`Awesome Scala <https://github.com/lauris/awesome-scala>`_

Tooling
*******

`conscript <http://www.foundweekends.org/conscript/setup.html>`_
++++++++++++++++++++++++++++++++++++++++++++++++++++++

You can install Giter8 and other Scala command line tools with Conscript. This will setup Conscript in ~/.conscript/bin/cs:

.. code-block:: bash

   curl https://raw.githubusercontent.com/foundweekends/conscript/master/setup.sh | sh



.. _giter8:

`giter8 <http://www.foundweekends.org/giter8/>`_
+++++++++++++++++++++++++++++++++++++++++++++++++++

install conscript first
A simple template with scalatest

.. code-block:: bash

   cs foundweekends/giter8
   g8 fayimora/basic-scala-project 


`list of templates <https://github.com/foundweekends/giter8/wiki/giter8-templates>`_
   

Android
-------

`Andoid Studio <https://developer.android.com/studio/index.html>`_

http://blog.andresteingress.com/2011/09/20/programming-android-with-scala/


Multi-project build
-------------------

Multi-project build is not the strong point of sbt:
 - Child projects cannot be checked out and built independently. The build has to happen in the root project. 
 - no reuse from one `build.sbt` to the other. For this you have to use `project` directory of the root project, and define regular scala files:

See the `Akka build <https://github.com/akka/akka/blob/master/project/AkkaBuild.scala>`_ and the giter8 templates for multi module project.


Concepts
********************

.. toctree::

   sbt
   Di
   ParallelProgramming

library
********************

Index many scala libraries.
`Scaladex <https://index.scala-lang.org>`_

.. toctree::

  libraries
  testing


Static Analysis Tool
*********************

.. toctree::

  staticAnalysis
