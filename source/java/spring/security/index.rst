Security
===========

.. code-block:: java
   :caption: authenticate()
	     
   AuthenticationManager am = SpringFactory.getBean(AuthenticationManager.class);
   Authentication authentication = new UsernamePasswordAuthenticationToken("bob", "bobspassword");		
   am.authenticate(authentication);

.. figure:: uml/UserDetails.png

   Accessing UserDetails
   
.. figure:: uml/architecture.png

   AuthenticationManager

	    
.. figure:: uml/authenticationManagerBuilder.png

   authenticationManagerBuilder

   Need to import 
   ObjectPostProcessorConfiguration
   
   EnableGlobalMethodSecurity
