===========================
Git Basics: Ab in die Shell
===========================

.. figure:: /_static/gitcloud.png
   :class: fill






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
