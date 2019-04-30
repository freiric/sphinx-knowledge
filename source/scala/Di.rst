Dependency Injection
=============

 - `Jonas Boner Real World Scala Dependency Injection <http://jonasboner.com/real-world-scala-dependency-injection-di>`_
 - `Adam Warski's Mac Wire <http://di-in-scala.github.io/>`_
 - `<http://www.andrewrollins.com/2014/08/07/scala-cake-pattern-self-type-annotations-vs-inheritance/>`_

Cake Pattern
************

We want to modify the behaviour of  a class A by mixing it with different implementations of a trait B. The trait B should have access to A.

With explicit typed self-reference, the implementations of B have access to the methods and variables of A.

.. code-block:: scala

   trait A extends B {
     def valInA = ...
     type Helper
     // use b()
     def a()= ...
     
   }
   
   trait B { this:  A =>
      def b(): Helper   
   }

   trait BImpl {
      def b() = {
         // use a()
      }
   }
   
   object AWithBImpl extends A with BImpl

Let us try to achieve the same result without explicitly typed self reference.


.. code-block:: scala

   trait A extends B {
     def a() = ...
     type Helper
     // use b()
     def method()= ...
     
   }
   
   trait B { this:  A =>
      def b(): Helper   
   }

   trait BImpl {
      def b() = {
         // use a()
      }
   }
   
   object AWithBImpl extends A with BImpl
