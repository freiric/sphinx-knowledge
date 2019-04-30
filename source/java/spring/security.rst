Spring
======

Boot
+++++++++
Actuator
*********
Add access point on web service to check met property as health

Spring cloud
++++++++++++++++++++

Spring coud config
*******************

Spring cloud tasks
*******************

Web
+++++

Security
++++++++

.. code-block:: java
   :caption: authenticate()
	     
   AuthenticationManager am = SpringFactory.getBean(AuthenticationManager.class);
   Authentication authentication = new UsernamePasswordAuthenticationToken("bob", "bobspassword");		
   am.authenticate(authentication);

.. figure:: uml/UserDetails.jpg

   Accessing UserDetails
   
.. figure:: uml/architecture.jpg

   AuthenticationManager

	    
.. figure:: uml/authenticationManagerBuilder.jpg

   authenticationManagerBuilder

   Need to import 
   ObjectPostProcessorConfiguration
   
   EnableGlobalMethodSecurity
