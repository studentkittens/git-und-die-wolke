=======================
Github: Ab in die Wolke
=======================

.. figure:: /_static/gitcloud.png
   :class: fill

----------------
Was kann Github?
----------------

- Für Open-Source kostenlos.

   - Einschränkungen: 2 GB Speicherplatz.

- Infrastructure as a Service
- Für Unternehmen gibt es ``private repos``.
- Für große Unternehmen kann man die Github-Software lizensieren.
- Eigener Pastebin mit Versionierung: ``Gist``.
- Volltextsuche über alle Repositories.


Demo: Nutzerprofil
------------------

- Git kennt nur den namen und email des Nutzers.

.. code-block:: bash

    # Wird in ~/.gitconfig gespeichert
    $ git config --global user.name "John Doe"
    $ git config --global user.email johndoe@example.com

- Github kennt unabhängig davon noch einen Account.
- Diesem sind ``1..n`` Repository zugeordnet. 
- Zudem kann dieser User andere Projekte Forken, BugReports schreiben u.v.m


Demo: Fork
----------

- Ein Fork ist ein ``git clone`` mit anderen Namen.
- Man klont ``user_a/repo.git`` zu ``user_b/repo.git``.
- Dann macht man den Code den man geforkt hat kaputt.
- Wenn man fertig (mit der Welt) ist kommt ein **Pull Request**.

Demo: Pull Requests
-------------------

Ablauf ohne Github:

.. code-block:: bash

    # Auf Seite des Forkers (user_b)
    $ git request-pull HEAD^1 https://github.com/<user_b>/repo.git > mail
    The following changes since commit 04ca9db3149956ed7670d699cb4b4328386b88e1:
      Sophisticated Commit Message. (2013-05-11 00:36:56 +0200)

    are available in the git repository at:
      https://github.com/<user_b>/repo.git master

    # Auf Seite des Annehmers (user_a)
    $ git remote add user_b https://github.com/<user_b>/repo.git
    $ git pull user_b 

Ablauf mit Github:

    - ``user_b`` macht über Github einen Pull Request.
    - ``user_a`` klickt auf ``Confirme Merge``.


Demo: Organisationen
--------------------

- Ein leichter Weg um Teams zu organisieren.
- Eine **Organisation** ist ein eigenständiger Nutzer.
- 

Demo: Sonstiges #1
------------------

- **Issuetracker:**

    - Eingebauter Bugtracker_.

- **Metriken:**

    - ``Contributors``, ``Commit Activity``, ``Pulse``.
    - Beispiel_.

- **Downloads:**

    - Gepushte Tags werden als Download_ angeboten.
    - Beispiel: Anlegen von ``1.2.0rc1``:

    .. code-block:: bash

        $ git tag 1.2.0rc1
        $ git push origin 1.2.0rc1

    - 
regel
.. _Beispiel: https://github.cngstom/sahib/glyr/contributors
.. _Bugtracker: https://github.com/sahib/glyr/issues
.. _Download: https://github.com/sahib/glyr/tags

Demo: Sonstiges #2
------------------

- **Wiki/Webpagehosting:**

    - Leicht erstellbares wiki.
    - ``gh-pages`` branch wird unter ``<user>.github.io/<repo>`` gehosted.
    - Beispiel: http://sahib.github.io/rmlint/

- **Soziales:**

    - Andere user kann man ``followen``. 
    - Andere repos kann man ``watchen``.
    - Anzeige von Aktivitäten anderer auf dem Dashboard_.

.. _Dashboard: https://github.com/

-------------
``git hooks``
-------------


Demo: Hooks
------------
  
  - Twitter (https://twitter.com/cloudkittens)
  - TravisCI
  - ReadTheDocs

  - Buildhook
  - Bugzilla
  - Metriken 
  - Email-Hook
