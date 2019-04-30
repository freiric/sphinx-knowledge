TEST
=======

A explorer:

- testng
- junit5 alias jupiter
- `DBUnit <http://dbunit.sourceforge.net/>`_
- `unitils <http://www.unitils.org/summary.html>`_
- `flyway <https://flywaydb.org/>`_
- oracle in docker container
- `assertj <https://joel-costigliola.github.io/assertj/assertj-swing.html>`_
fork of FEST (https://www.ibm.com/developerworks/library/j-swingtest/index.html#artrelatedtopics)
- `The Grinder <http://grinder.sourceforge.net/>`_
  
  https://github.com/swingexplorer/swingexplorer/
  http://robotframework.org/

TestNG vs JUnit
****************

1.  JUnit still requires the before/after class methods to be static, which limits
    what you can do prior to the running of tests, TestNG never has this issue.

2.  TestNG @Configuration methods can all take an optional argument to their 
    annotated methods in the form of a ITestResult, XmlTest, Method, or 
    ITestContext.  This allows you to pass things around that JUnit wouldn't 
    provide you.  JUnit only does this in listeners and it is limited in use.

3.  TestNG comes with some pre-made report generation classes that you can copy
     and edit and make into your own beautiful test output with very little 
     effort. Just copy the report class into your project and add a listener 
     to run it.  Also, ReportNG is available.

4.  TestNG has a handful of nice listeners that you can hook onto so you can do
     additional AOP style magic at certain phases during testing.

Spring
*******

spring-test `Spring TestContext Framework <https://docs.spring.io/spring/docs/current/spring-framework-reference/testing.html#testcontext-framework>`_

`Parameterized JUnit tests and Spring contexts <https://beautifulbytes.wordpress.com/2015/07/30/parameterized-junit-tests-and-spring-contexts/>`_

.. code-block:: java

   testContextManager = new TestContextManager(getClass());
   testContextManager.prepareTestInstance(this);
