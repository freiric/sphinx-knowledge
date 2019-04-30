Tooling
=======

Cask
****

`Cask <https://github.com/cask/cask>`_

To develop with cask, you need a ``Cask`` file at the root of the project listing all the dependencies of the project.

.. code-block:: bash

   cask exec emacs --debug-init --quick  -l my-project.el&


Pallet
******

`Pallet <https://github.com/rdallasgray/pallet>`_

While ``package.el`` is the standard way to install new package in emacs, they can be listed and installed in Cask (in ``~/.emacs.d/Cask``) too, `Pallet <https://github.com/rdallasgray/pallet>`_ hook into ``package.el`` the list of managed packaged in Cask from it.

Run ``M-x pallet-init`` after installation of pallet (through ``M-x package-install pallet``), and you should see your ``~/.emacs.d/Cask`` updated.

