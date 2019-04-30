Maven And Tycho
===============

Build Modularization
++++++++++++++++++++

Modularization of software is important to allow easier improvement/replacement of a module without having to rework the whole application. This modularization can be defeated by a monolithic build. If in course of the development for a particular module, I have to rebuild the whole stack, this will take ages and lead to early discouragment. So the Build too has to be modular.

Let us see how to to achieve Build modularity with Tycho. 

Packaging types
++++++++++++++++++++++

Tycho defines new Maven `packaging types <http://wiki.eclipse.org/Tycho/Packaging_Types>`:

- eclipse-plugin
    produces jar with osgi manifest, and installs them in the local maven repo with some OSGi metadata.
- eclipse-test-plugin
    runs test in an OSGi environment.
- eclipse-feature
    creates feature, i.e. eclipse specific description of set of plugin
- eclipse-repository
    materializes data needed to create a p2 update site
- eclipse-target-definition
    creates a target definition, i.e. the set of plugin forming the classpath of the current eclipse workbench

We will shy away from the eclipse-target-definition because the target platform generator of Cerner is better at supplying the accompanying source code. 

