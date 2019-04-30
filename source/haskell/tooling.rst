Tooling
==========

Stack uses stackage snapshot (collectiosn of packages)

Stack
*****

`Stack manual <https://docs.haskellstack.org/en/stable/README/>`_

Create new project

.. code-block:: bash

   stack new   ## setup new project
   stack setup ## download compiler if needed

compile and run

.. code-block:: bash

   stack build        ## build the project
   stack exec my-exec ## executes the comiled executable

Cabal
*****

`Cabal user guide <https://www.haskell.org/cabal/users-guide/index.html>`_

Install package `cabal install`

.. code-block:: bash

   cabal update
   cabal install -j pandoc

configure, build, test


.. code-block:: bash 

   cabal configure
   cabal build

   cabal configure --enable-tests
   cabal build

   cabal test

create a new project

.. code-block:: bash 

   cabal init
   mkdir src
   
in the section ``library`` add ``hs-source-dirs:      src``.

sandbox
+++++++

`caldwaste <http://coldwa.st/e/blog/2013-08-20-Cabal-sandbox.html>`_

.. code-block:: bash

   $ cd /path/to/my/haskell/library
   $ cabal sandbox init                   # Initialise the sandbox
   $ cabal install --only-dependencies    # Install dependencies into the sandbox
   $ cabal build     

Search for installed package information

.. code-block:: bash

   $ cabal sandbox hc-pkg list aeson


`ghc-pkg <https://wiki.haskell.org/Ghc-pkg>`_
*********************************************

- list installed package
- remove package

Emacs
*****

Haskell-mode
++++++++++++

.. code-block:: bash

   M-x haskell-process-generate-tags

`Flycheck <https://www.flycheck.org/en/latest/languages.html>`_
****************************************************************

`flycheck-haskell <https://github.com/flycheck/flycheck-haskell>`_

Have a stack in your path if you want to use stack...

.. code-block:: shell

   export PATH="~/.cabal/bin:$PATH"


Cask
****
`SHM<https://github.com/projectional-haskell/structured-haskell-mode>`_
************************************************************************


Hdevtools
++++++++++
Does not read the cabal configuration

Scion 
++++++++++

Hlint 
++++++++++

Ghc-mod 
++++++++++

Eclipsefp 
++++++++++

GHCi 
++++++++++

.. code-block:: bash

   ghci -optP-include -optPdist/build/autogen/cabal_macros.h

.. code-block:: haskell

   fun :: a -> a
   fun a = a
