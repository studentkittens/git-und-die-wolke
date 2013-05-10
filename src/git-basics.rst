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

      http://www.youtube.com/watch?v=4XpnKHJAok8

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

* Url-Shema Beispiele: ::
   
     git://github.com/qitta/foozel.git         → Git [Read only]
     git@github.com:sahib/rmlint.git           → SSH [Preferred]
     https://github.com/tmarc/advanced-ios.git → HTTPS [Notlösung]
     git clone file:///opt/git/project.git     → Lokal 


-----------
``git add``
-----------

.. code-block:: bash

   $ git add [your-file-or-dir-here]

.. image:: /_static/untracked_to_staged.png
   :align: center

[Noch] Einfacher dargestellt:

    http://ndpsoftware.com/git-cheatsheet.html


-----------------
``git commit #1``
-----------------

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

-----------------
``git commit #2``
-----------------

Früher oder später will man etwas berichtigen

.. code-block:: bash

    # Letzte commit messages berichtigen
    # to amend == berichtigen.
    $ git commit --amend

.. code-block:: bash

    # änderungen an einem file zurücksetzen
    # Working Tree -> Unmodified
    git checkout -- your_file.txt

.. code-block:: bash

    # "git add" rückgängig machen
    # Index -> Working Tree
    git reset your_file.txt


-----------------
``git remote #1``
-----------------
   
.. rst-class:: build

- Bis jetzt passierte alles lokal.
- Bis auf ``git clone``.

.. image:: /_static/central.png
    :align: center
    :width: 70%

-----------------
``git remote #2``
-----------------

Und jetzt dezentral:

.. image:: /_static/decentral.png
    :align: center
    :width: 70%

-----------------
``git remote #3``
-----------------

Und jetzt in ``Git-Speak``?

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

-----------------
``git bisect #1``
-----------------

Aus ``man git-bisect``: 

    ``Find by binary search the change that introduced a bug``

**Aufgabe:**

    - Finde heraus wann ein Fehler eingefürt wurde.
    - Schaue dir an was damals geändert wurde.
    - Leite daraus ab was der Fehler ist.

**Funktionsweise:**

    - Festlegen eines good/bad commits
    - Auschecken der Mitte, Testen, Links oder Rechts weitersuchen.

-----------------
``git bisect #2``
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

Testcase:

.. code-block:: c

    void test_is_odd(void) {
        for(int i = -20; i < 20; ++i) {
            assert(is_odd(i) == (i % 2 == 1));
        }
    }

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

    * Immer kleine commits machen!
    * Nehmt euch Zeit für eine *sinnvolle* Commit-Messages! Schlechte Beispiele
      (**\***):

        - **Some changes** - Riesiger diff.
        - **minor changes** - Complete Rewrite.
        - **Merge.** - Manuelles Merging.
            
    * ``git bisect`` ist ein gutes Argument für Unit-Tests.

\* (*Noch mehr davon:* http://whatthecommit.com/)


--------------
Best Practices
--------------

- .gitignore
- kein autogen
- ...
