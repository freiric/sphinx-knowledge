`SBT <http://www.scala-sbt.org/>`_
++++++++++++++++++++++++++++++++++

update sbt
-----------

create a directory and a file in a  subdirectory ``project/build.properties`` with ``sbt.version=0.13.13``


scaffolding a new project
-------------------------

see `giter8 <index.html#giter8>`__.

from sbt 013.13, with ``new`` command

.. code-block:: bash
   
   sbt new fayimora/basic-scala-project 


print dependencies
-------------------

Creates an ivy file in `target/scala-2.10/ivy-0.4-SNAPSHOT.xml`

.. code-block:: bash
   
   sbt deliver-local

eclipse file generation
-----------------------

See `sbteclipse <https://github.com/typesafehub/sbteclipse/wiki/Using-sbteclipse>`_

To avoid generation of non-existing  source directory (this can be a problem for generated source directory?), set in a central config file in `~/.sbt/0.13/conf.sbt` or `~/.sbt/conf.sbt`

.. code-block:: bash

   unmanagedSourceDirectories in Compile ~= { _.filter(_.exists) }

   unmanagedSourceDirectories in Test ~= { _.filter(_.exists) }

The `ivyde plugin <http://ant.apache.org/ivy/ivyde/>`_. I was looking for a way to pack all my dependencies in a same classpath container but after installing this plugin and regenerating the eclipse conf files with sbteclipse, it did happen automatically (in a classpathcontainer named referenced libraries in eclipse).

.. code-block:: bash

   sbt deliver-local

The ``ivy.xml`` file is in ``target/scala-X.XX``.
