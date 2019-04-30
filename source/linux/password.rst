Password management
=====================

Expect
******

Sudo
****

SSH
****

Shell Login
-----------

Check that the user `/etc/passwd` does not contain `/sbin/nologin`.
ssh-keygen -t rsa
ssh-copy-id fb019397@192.168.1.8

keychain allows to use ssh-agent across different session (password needed only on reboot)
`keychain <http://www.ibm.com/developerworks/linux/library/l-keyc2/>`_
keychain can manage the gpg-agent as well

.. code-block:: bash

   keychain --agents ssh,gpg  ~/.ssh/id_rsa ~/.ssh/id_dsa D2BE32D5
   source ~/.keychain/$(hostname)-sh > /dev/null
   source ~/.keychain/$(hostname)-sh-gpg > /dev/null

To avoid having another instance of ssh-agent running:

- cp /run/current-system/sw/etc/xdg/autostart/gnome-keyring-ssh.desktop
  ~/.config/autostart
  echo Hidden=true >> ~/.config/autostart/gnome-keyring-ssh.desktop
- comment out ``#use-ssh-agent`` in ``/etc/X11/Xsession.options``
- append ``.inactive`` to ssh-agent startup script ``/etc/X11/Xsession.d/``
- remove systemd config: (https://wiki.archlinux.org/index.php/Systemd/User)
  ``~/.config/systemd/user/ssh-agent.service``
  
GPG
*****

find key id, ``seahorse`` or

.. code-block:: bash

   gpg -k
		
Password manager are mainly based on pgp, disadvantage are

  - one need to convince people to get a pgp-key
  - one need to export one's pgp secret key on the remote machine
    
`pass <https://www.passwordstore.org/>`_

PAM - Pluggable Authentication Modules
**************************************

  `pam <http://www-igm.univ-mlv.fr/~dr/XPOSE2003/augereau/2.html>`_

Other: Kerberos
****************
