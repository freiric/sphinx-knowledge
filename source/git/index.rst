GIT
====

Add a remote
************

Add a remote with a tracking branch, allow to ``git pull`` and ``git push`` without having to pecise ``git pull origin master``

.. code-block:: bash

   git remote add mynewremote https://github.com/user/repo.git
   git branch -u mynewremote
   ## if the branch already exists, pass the option -u or --set-upstream to the push command
   git push -u mynewremote

..
		git branch -u https://github.com/freiric/repo.git

Visual Cheat Sheet
*******************

http://ndpsoftware.com/git-cheatsheet.html#loc=workspace;

Split a commit
***************

.. code-block:: bash

    git cherry-pick …
    git rebase origin/master -i
    # dort e statt pick
    # commit id merken
    git reset HEAD^
    git add -p
    git commit -m „erster commit“
    git add -p
    git commit -m „zweiter commit“
    git rebase —continue
    # selbiges mit dem zweiten commit
    # commit id merken
    # dann kannste mit „git commit -c commitId“ die alte commit-id verwenden
    # wenn es sinn macht
    git commit -C commitid 


    
