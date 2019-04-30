Gradle
======

Gradle is a groovy based build tools. The **gradle** command looks for a file called **build.gradle** in the current directory.

.. code-block:: groovy
 
 task hello {
     doLast {
         println 'Hello world!'
     }
 }


Task dependency and :samp:`<<` shortcut:

.. code-block:: groovy

 task hello << {
     println 'Hello world!'
 }
 task intro(dependsOn: hello) << {
     println "I'm Gradle"
 }

Java
....

.. code-block:: shell

  gradle setupBuild
  mkdir -p src/main/java src/test/java src/main/resources src/test/resources

uncomment your freshly created **gradle.build** file and run:

.. code-block:: shell

  gradle build


