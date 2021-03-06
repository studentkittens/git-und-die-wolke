.. _git_basics: 

===========================
Git Basics: Ab in die Shell
===========================


.. figure:: /_static/gitcloud.png
   :class: fill

--------------
 Was ist git?
--------------

    * Ein Versionsverwaltungssystem
    * Ein Protokoll
    * Ein abstraktes Filesystem
    * Linus: ``A distributed stupid content tracker``

**Was ist es nicht?**

    * CVS (``WWCVSND``)
    * SVN (``CVS done right.``)

**Erklärung:**

      Linus on GoogleTalk_.


.. _GoogleTalk: http://www.youtube.com/watch?v=4XpnKHJAok8&t=8m20s

------------------
Zentraler Workflow
------------------
   
.. rst-class:: build

- Zentraler Workflow wie bei CVS
- Viele Entwickler arbeiten mit einem Repository
- Jeder Entwickler hat nur eine unvollständige Kopie

.. image:: /_static/central.png
    :align: center
    :width: 100%

--------------------
Dezentraler Workflow
--------------------
   
.. rst-class:: build

- ``git`` typischer Ablauf.
- Jeder Entwickler hat ein Repository
- Jeder Entwickler hat eine volle Kopie

.. image:: /_static/decentral.png
    :align: center
    :width: 105%

--------------
``git init``
--------------

* Lege ein neues Git-Repository in ``your-repo`` an.

.. code-block:: bash

    $ mkdir your-repo && cd your-repo
    $ git init .
    $ ls --all
    .  ..  .git
    $ tree .git
    .git
    ├── branches
    ├── config
    ├── HEAD
    ├── index
    ├── [...]
    ├── logs
    │   ├── HEAD
    │   └── refs
    ├── objects
    └── refs

-----------
``git add``
-----------

.. code-block:: bash

   $ git add [your-file-or-dir-here]

.. image:: /_static/untracked_to_staged.png
   :align: center
   :width: 80%

Alle Bereiche interaktiv als HTML:

    http://ndpsoftware.com/git-cheatsheet.html

--------------
``git commit``
--------------

.. code-block:: bash

   $ echo "Hello Phil!" > README
   $ git add README

.. code-block:: bash

   $ git status
   # On branch master
   # Changes to be committed:
   #   new file:   README

.. code-block:: bash

   $ git commit --all --message "commit message"  # ausgechrieben
   $ git commit -am "commit message"              # oder kürzer
   $ git commit -a                                # lange messages
   [Editor öffnet sich]

.. code-block:: bash

   $ git status
   # On branch master
   nothing to commit, working directory clean

---------------------
Was ist ein ``diff``?
---------------------

.. rst-class:: build

- Ein ``diff`` ist die Änderung zwischen zwei Änderungen.
- Errr… Wat?

    .. code-block:: bash

        # Zeige alle Änderungen seit dem letzten Commit
        $ git diff
        diff --git a/TODO.list b/TODO.list
        index e6c2b18..a2fe0bc 100644
        --- a/TODO.list
        +++ b/TODO.list
        @@ -1,21 +1,20 @@
        +✓ Hinweise in der Versionshistorie verstecken  
        -✓ Zettelchen schreiben

    .. code-block:: bash

        # Bestimmten Commit zeigen
        $ git show a2fe0bc
        <dasselbe wie oben>


--------------------------
Freunde von ``git commit``
--------------------------

Früher oder später will man etwas berichtigen

.. code-block:: bash

    # Letzte Commit-Messages berichtigen
    # to amend == berichtigen.
    $ git commit --amend

.. code-block:: bash

    # Änderungen an einem file zurücksetzen
    # Working Tree -> Unmodified
    $ git checkout -- your_file.txt

.. code-block:: bash

    # "git add" rückgängig machen
    # Index -> Working Tree
    $ git reset your_file.txt

.. code-block:: bash

    $ git stash       # Änderungen kurz wegsichern
    $ git stash pop   # … später wieder hervorholen



----------------------
Die Objektdatenbank #1
----------------------

Vier unterschiedliche Objekttypen: 

* Blobs (Dateien)
* Trees (Verzeichnisse)
* Commits (Änderungen)
* Referenzen (Branches oder Tags)

.. image:: /_static/simple_tree.png
   :align: center
   :width: 60%

----------------------
Die Objektdatenbank #2
----------------------

.. image:: /_static/simple_commit.png
   :align: center
   :width: 100%

----------------------
Die Objektdatenbank #3
----------------------

.. image:: /_static/simple_branch.png
   :align: center
   :width: 100%

-------------
Git Branching
-------------


.. figure:: /_static/branch.png
    :align: center
    :class: fill

-----------
Branches #1
-----------

Branches erstellt man mit:

.. code-block:: bash

    $ git checkout -b <branch-name> 

In bestehende branches wechseln:

.. code-block:: bash

    $ git checkout <branch-name>

Branches auflisten:

.. code-block:: bash

    $ git branch --all

-----------
Branches #2
-----------

Branches führt man zusammen mit:

.. code-block:: bash

    $ git merge <target-branch>

.. rst-class:: build

- Dabei können böse Dinge passieren.
- Dinge die ``git``-Anfänger zu CVS-Usern werden lässt.
- Es können **Merge-Conflicts** entstehen.
- Was passiert wenn in beiden ``branches`` dasselbe File geändert wurde?

    - Andere Zeile? ``git`` merged es automatisch. 
    - Selbe Zeile? Uh-oh.

--------------
``git clone``
--------------

* Klone ein Repository

.. code-block:: bash

    $ git clone git://github.com/studentkittens/git-und-die-wolke.git

    Cloning into 'git-und-die-wolke'...
    remote: Counting objects: 94, done.
    remote: Compressing objects: 100% (72/72), done.
    remote: Total 94 (delta 36), reused 72 (delta 16)
    Receiving objects: 100% (94/94), 5.70 MiB | 1.60 MiB/s, done.
    Resolving deltas: 100% (36/36), done.

* URL-Schema Beispiele: ::
   
     git://github.com/qitta/foozel.git         → Git [Read only]
     git@github.com:sahib/rmlint.git           → SSH [Preferred]
     https://github.com/tmarc/advanced-ios.git → HTTPS [Notlösung]
     git clone file:///opt/git/project.git     → Lokal 

--------------
``git remote``
--------------

Entfernte Repositories verwalten:

.. code-block:: bash

    # Alle remotes auflisten
    $ git remote -v
    origin  git@github.com:studentkittens/git-und-die-wolke.git (fetch)
    origin  git@github.com:studentkittens/git-und-die-wolke.git (push)

.. code-block:: bash

    # Neues remote adden
    $ git remote add nullcat git@nullcat.de
    $ git remote -v
    …
    nullcat git@nullcat.de (fetch)
    nullcat git@nullcat.de (push)

.. code-block:: bash

    # Bestehendes remote verändern
    $ git remote set-url nullcat https://git.nullcat.de

------------
``git push``
------------

.. code-block:: bash

    $ git push [<remote> [<local-branch>]]

.. code-block:: bash

    $ git push
    $ git push origin
    $ git push origin master
    

.. image:: /_static/push.jpg
    :align: center
    :width: 45%

------------
``git pull``
------------

.. rst-class:: build

- Das logische Äquivalent zu ``git push``.
- Zieht Änderungen von einem **remote**.

    .. code-block:: bash

        $ git pull <remote> <remote-branch>

- Auch hier können **Merge-Conflicts** entstehen.
- Vor einem ``git push`` sollte man immer ein ``git pull`` machen.

-------
Hilfe?!
-------

.. rst-class:: build

- Das ist ja alles schön und gut…
- …aber ich versteh kein Wort.

- Hier wirst du geholfen:

    - manpages: 

      .. code-block:: bash

         $ git help <commando>
         $ git help tutorial

    - http://www.git-scm.com/documentation
    - http://de.gitready.com/
    - Es gibt eine Menge Bücher.



-----------------
``git bisect #1``
-----------------

Source:

.. code-block:: c

    bool is_odd(int number) {
        return !number % 2; /* Wrong! */
    }

    int main(int argc, char *argv[]) {
        printf("Odd numbers of arguments? %d!\n",
            is_odd(argc - 1) ? "Yes" : "No");
    }

Test case:

.. code-block:: c

    void test_is_odd(void) {
        for(int i = -20; i < 20; ++i) {
            assert((is_odd(i) != 0) == (i % 2 != 0));
        }
    }

-----------------
``git bisect #2``
-----------------

    ``Find by binary search the change that introduced a bug``

**Aufgabe:**

    - Finde heraus wann ein Fehler eingeführt wurde.
    - Schaue dir an was damals geändert wurde.
    - Leite daraus ab was der Fehler ist.

**Funktionsweise:**

    - Festlegen eines good/bad commits
    - Auschecken der Mitte, Testen, Links oder Rechts weitersuchen.


-----------------
``git bisect #3``
-----------------

.. code-block:: bash

    $ git bisect start HEAD HEAD^^^ 
    $ git bisect run make test      
    # ... viel output von $(make test) ...
    5145c8 is the first bad commit
    'bisect run' erfolgreich ausgeführt
    $ git bisect reset    # Kehre zur normalen Arbeit zurück
    $ git show 5145c8     # Zeige unterschiede im bad commit
    commit 5145c8781e30057c8e2058d1c361363e213a17f4
    Date:   Fri May 3 15:47:38 2013 +0200

        Made is_odd() better looking

    diff --git a/is_odd.c b/is_odd.c
     
     bool is_odd(int number)
     {
    -    return number % 2 == 1;
    +    return !number % 2;
     }

-----------------
``git bisect #4``
-----------------

Was lernt man draus?

    * Immer kleine Commits machen!
    * Nehmt euch Zeit für eine *sinnvolle* Commit-Messages! Schlechte Beispiele
      (**\***):

        - **Some changes** - Riesiger diff.
        - **minor changes** - Complete Rewrite.
        - **Merge.** - Manuelles Merging.
            
    * ``git bisect`` ist ein gutes Argument für Unit-Tests.

\* (*Noch mehr davon:* http://whatthecommit.com/)

-----------------------
Suchen und Beschuldigen
-----------------------

Suche ``background:`` in allen ``.css`` Dateien. 

.. code-block:: bash

    $ git grep -n 'background:' -- '*.css'
    src/custom.css:56: background: -webkit-radial-gradient(#9cf, #369);
    src/custom.css:57: background:    -moz-radial-gradient(#9cf, #369);
    src/custom.css:58: background:         radial-gradient(#9cf, #369);

Herausfinden wer wann etwas geändert hat:

.. code-block:: bash

    $ git blame -L 56,58 src/custom.css
    # SHA1   (Autor LN) Content
    77a79bbc (Elch  56) background: -webkit-radial-gradient(#9cf, #369);
    64ac73cb (Katze 57) background:    -moz-radial-gradient(#9cf, #369);
    77a79bbc (Elch  58) background:         radial-gradient(#9cf, #369);

→ Der Autor ``Katze`` ist für den Mozilla-Support zuständig.

-----------
``git tag``
-----------

- Manchmal muss man einen Commit *taggen*.
- Wie ``branches``, nur *fest*.
- Beispielsweise mit einer Version: **1.2 beta**

    .. code-block:: bash 

        # Neuen Tag anlegen
        git tag "1.2 beta"

    .. code-block:: bash

        # Alle Tags auflisten
        git tag

    .. code-block:: bash 

        # Anderes Tag löschen.
        git tag -d "1.2 beta"

    .. code-block:: bash 

        # Tags "veröffentlichen"
        git push origin <local-tag-name>

-----------------------------
Das GitFlow Branching Modell 
-----------------------------

.. figure:: /_static/gitflow.png
    :class: fill
    :width: 70%

---
...
---


.. figure:: /_static/yoda.png
    :class: fill 
    :width: 20%

-------
Tooling
-------

**Plugins**

* GVim Fugitive Plugin
* Eclipse EGit
* Netbeans (bereits integriert)

**Standalone Tools**

* gitg (Linux / Gnome)
* giggle (Portabel / Gnome)
* tig (Linux / ncurses)
* gitk (bereits in git enthalten)
* GitHub Windows Client


-----------------
Best Practices #1
-----------------

.. rst-class:: build

- ``.gitignore`` nutzen (und ``git clean``!).
  
    - Keinen auto generierten Code/Projektdateien committen.
    - Wenn nicht vermeidbar dann in eigenen Commit.
    - Für Dokumentation am besten eigenen Branch nutzen!

- Sinnvolle Commit-Messages.

    - Siehe Folie für ``git bisect 4``.

-----------------
Best Practices #2
-----------------

.. rst-class:: build

- Ein Feature == Ein Commit.

    - Macht Debugging/Übersicht einfacher.

- Review Code before commit.

    - Keine ``Fixed up previous commit`` Messages.

- Branches für Features nutzen.

    - Damit der ``master`` branch benutzbar bleibt.

--
……
--

.. figure:: /_static/af.jpg
   :class: fill

-------------
``git fetch``
-------------

.. rst-class:: build

- ``git pull`` ist ein ``git fetch && git merge``.
- Warum sollte man das wollen?
- Wenn man nicht will dass automatisch gemerged wird.
- Beispiel: 

  .. code-block:: bash

    $ git fetch origin 
    $ git checkout origin/master
    $ # look around
    $ # if satisfied:
    $ git checkout master
    $ git merge origin/master


-----------------
``git rebase #1``
-----------------

Ausgangszustand:

.. image:: /_static/gitrebase-1.png
    :align: center
    :width: 80%

-----------------
``git rebase #2``
-----------------

Ohne Rebase, mit ``git merge``:

.. code-block:: bash

    $ git checkout master 
    $ git merge experiment

.. image:: /_static/gitrebase-2.png
    :align: center
    :width: 80%

-----------------
``git rebase #3``
-----------------

Mit Rebase: 

.. code-block:: bash

    $ git checkout experiment  # In 'experiment' wechseln
    $ git rebase master        # Basis auf master verschieben
    $ git checkout master      # In 'master' wechseln
    $ git merge experiment     # Fast-Forward Merge zu 'experiment'

.. image:: /_static/gitrebase-3.png
    :align: center
    :width: 90%

---
...
---

.. figure:: /_static/thanksobama.jpg
   :class: fill

----------------------------------------------
Ein Exkurs zu Storage as a Service mit ``git``
----------------------------------------------

|
|
|
|
|
|

SaaS mit ``git-annex``: :ref:`git_annex`
