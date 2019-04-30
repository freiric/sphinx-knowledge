Eclispe 4 
==========

Minimal application
-------------------

When following a tutorial to create an eclipse application, you are said to create a product, and magically everything works as expected.
If you already tried to create your own application, and some of the steps did differ a bit from the tutorial, I bet it has not worked just as magically, and you may have lost hours or even days trying to figure out what the hell did mean:

  java.lang.RuntimeException: No application id has been found.
  
or...

If you have been in such situation, hold on. The following is meant to be more than a more tutorial. The goal of this document is to give you enough understanding to allow you to build your own app and interpret what the heck eclipse is spitting out instead of running your baby flowlessly.


Headless
........

To define an eclipse application, we will need some OSGi bundle, the most important one is the framework plugin (in OSGi terminology, it is referenced as the system plugin).

- org.eclipse.osgi

With this plugin, we would have a running OSGi framework, but we want an eclipse application. We want to be able to use the plugin.xml or use any eclipse plugin. 
 so we need a bit more.

- org.eclipse.core.runtime

  - org.eclipse.equinox.common
  - org.eclipse.core.contenttype
  - org.eclipse.core.jobs
  - org.eclipse.equinox.app
  - org.eclipse.equinox.preferences
  - org.eclipse.equinox.registry

The OSGi application
....................

org.eclipse.equinox.app.IApplication

 .. code-block:: java

  package fr.cerner.rcp.osgi;

  ...

  public class Application implements IApplication {

	  public Object start(IApplicationContext context) throws Exception {
		  System.out.println("my app starting");
		  return null;
	  }

	  public void stop() {
		  System.out.println("my app stopping");
	  }

This application is rgistered in the plugin.xml:

 .. code-block:: xml

   <extension
         id="fr.cerner.rcp"
         point="org.eclipse.core.runtime.applications">
      <application
            cardinality="singleton-global"
            thread="main"
            visible="true">
         <run
               class="fr.cerner.rcp.osgi.Application">
         </run>
      </application>
   </extension>


Product
.......

The product is used in two places:

- In the plugin.xml of your plugin. There it is an extension point:

This extension point references an application id under the attribute application which in turn is defined in its own extension.

 .. code-block:: xml

    <extension
	  id="dmpProd"
	  point="org.eclipse.core.runtime.products">
       <product
	     application="fr.cerner.rcp.gui"
	     name="dmp">
       </product>
	   <property
		 name="appName"
		 value="My App Name">
	   </property>
	   ...
    </extension>

- In a file with an extension ".product".

 .. code-block:: xml

  <product name="dmp" uid="fr.cerner.rcp.gui.prod" id="fr.cerner.rcp.gui.dmpProd" application="fr.cerner.rcp.gui" 
           version="0.0.1.qualifier" useFeatures="true" includeLaunchers="true">


     <configIni use="default">
     </configIni>

     <launcherArgs>
	<programArgs>-clearPersistedState</programArgs>
	<vmArgs>-Dosgi.noShutdown=true</vmArgs>
	<vmArgsMac>-XstartOnFirstThread -Dorg.eclipse.swt.internal.carbon.smallFonts</vmArgsMac>
     </launcherArgs>

     <windowImages/>

     <splash
	startupProgressRect="5,275,445,15"
	startupMessageRect="7,252,445,20"
	startupForegroundColor="000000" />
     <launcher name="dmpgui">
	<solaris/>
	<win useIco="false">
	   <bmp/>
	</win>
     </launcher>


     <vm>
	<linux include="false">org.eclipse.jdt.launching.JRE_CONTAINER/org.eclipse.jdt.internal.debug.ui.launcher.StandardVMType/JavaSE-1.6</linux>
     </vm>

     <features>
	<feature id="fr.cerner.dmp.feature.headlessosgi" version="0.0.1.qualifier"/>
	<feature id="fr.cerner.dmp.feature.gui" version="0.0.1.qualifier"/>
	<feature id="fr.cerner.dmp.feature.log" version="0.0.1.qualifier"/>
     </features>

     <configurations>
	<plugin id="org.eclipse.core.runtime" autoStart="true" startLevel="2" />
	<plugin id="org.eclipse.equinox.common" autoStart="true" startLevel="2" />
	<plugin id="org.eclipse.gemini.blueprint.extender" autoStart="true" startLevel="3" />
	<property name="eclipse.ignoreApp" value="false" />
	<property name="osgi.noShutdown" value="true" />
     </configurations>

  </product>


Features or Plugins
...................





Target Platform
...............

Classpath for eclipse to find OSGi bundles. It is the set of bundles used by eclipse to resolve against the bundles or packages dependencies written in your MANIFEST.MF. By default, it is the plugin directory in your eclipse installation. 

To ensure that this does not change fron one eclipse installation to another, you will have to change it! The target platform should be specific to the project or to the platform defined by your organization.

Warning
.......

com.springsource.org.aspectj.tools (seen with version 1.7.1) exports osgi (e.g. IApplication)

http://stackoverflow.com/questions/5528646/osgi-candidate-permutation-failed-due-to-a-conflict-between-imports

Missing dependency org.w3c.dom.css in SWT default product (3.8.1 SR1 RC1),
add javax.xml to your product

https://bugs.eclipse.org/bugs/show_bug.cgi?id=387869

