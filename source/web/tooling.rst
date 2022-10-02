Tooling
=======

Npm
++++++

One can use `Nvm - Node Version Manager - Simple bash script to manage multiple active node.js versions  <https://github.com/creationix/nvm>`_
configured with ``package.json``


`Webpack <https://webpack.github.io/docs/>`_  
++++++++++++++++++++++++++++++++++++++++++++++

Starters
*********

- https://github.com/wbkd/webpack-starter
-  `JHIPSTER <https://www.jhipster.tech/>`_
- https://ngx-rocket.com/home

Yarn vs npm
**************

Stand 2018, Yarn et Npm se reattrapent l'un l'autre -> a priori on a plus besoin de yarn...


node
****

node package manager **npm**

bower
*****

.. code-block:: bash

   sudo npm install -g bower

   {
     "name": "my-project",
     "version": "1.0.0",
     "main": "path/to/main.css",
     "ignore": [
       ".jshintrc",
       "**/*.txt"
     ],
     "dependencies": {
       "<name>": "<version>",
       "<name>": "<folder>",
       "<name>": "<package>"
     },
     "devDependencies": {
       "<test-framework-name>": "<version>"
     }
   }

`Grunt <https://gruntjs.com/>`_
++++++++++++++++++++++++++++++++++
