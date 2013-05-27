=======================
Github: Ab in die Wolke
=======================

.. figure:: /_static/gitcloud.png
   :class: fill

---------------
Was ist Github?
---------------

- Ein (Social-)Code-Hosting Dienst.

----------------
Was kann Github?
----------------

- Für Open-Source kostenlos.

   - Einschränkungen: 1 GB Speicherplatz.

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
- Man klont ``alice/example.git`` zu ``bob/example.git``.
- Dann macht man den Code den man geforkt hat kaputt.
- Wenn man fertig (mit der Welt) ist kommt ein **Pull Request**.

Demo: Pull Requests
-------------------

Ablauf ohne Github:

.. code-block:: bash

    # Auf Seite des Forkers (bob)
    $ git request-pull HEAD^1 https://github.com/<bob>/repo.git > mail
    The following changes since commit 04ca9db3149956ed7670d699cb4b4328386b88e1:
      Sophisticated Commit Message. (2013-05-11 00:36:56 +0200)

    are available in the git repository at:
      https://github.com/<bob>/repo.git master

    # Auf Seite des Annehmers (alice)
    $ git remote add bob https://github.com/<bob>/repo.git
    $ git pull bob 

Ablauf mit Github:

    - ``bob`` macht über Github einen Pull Request.
    - ``alice`` klickt auf ``Confirme Merge``.


Demo: Organisationen
--------------------

- Ein leichter Weg um Teams zu organisieren.
- Eine **Organisation** ist ein eigenständiger Nutzer.
- Grundlegender Ansatz bei Entwicklung mit mehreren Personen
  
**Features:**

Verwaltung von...

- Membern (ein GitHub User entspricht einem Member)
- Teams (Anlegen) 
- Rechten (Pull, Push, Admin)


Demo: Online Blame/Annotate/Edit
--------------------------------

- Code lässt sich online browsen.

Zudem anschaubar:

    History eines Files/Zeile
    Autoren
    ... TODO 


Demo: Sonstiges #1
------------------

- **Issuetracker:**

    - Eingebauter Bugtracker_.

- **Metriken:**

    - ``Contributors``, ``Commit Activity``, ``Pulse``.
    - Beispiel_.

- **Downloads:**

    - Gepushte Tags werden zu Downloads_.
    - Beispiel: Anlegen von ``1.2.0rc1``:

    .. code-block:: bash

        $ git tag 1.2.0rc1
        $ git push origin 1.2.0rc1

.. _Beispiel: https://github.cngstom/sahib/glyr/contributors
.. _Bugtracker: https://github.com/sahib/glyr/issues
.. _Downloads: https://github.com/sahib/glyr/tags

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

----------
Github-APi
----------

TODO


-------------
``git hooks``
-------------

- Mechanismus um in wichtige git-commandos einzuhaken 
- Meist kleine Shell-Scripte:

.. code-block:: bash

    $ echo "echo I am a hook." > .git/hooks/pre-commit
    $ git commit -am "some message"
    I am a hook.
    # Auf Zweig master
    # Ihr Zweig ist vor 'origin/master' um 3 Versionen.
    # ...

- Hooks werden durch bestimmte Namen identifiziert
    
    - ``pre-commit, prepare-commit-msg, commit-msg, post-commit``
    - ``pre-receive, update``


Demo: Cloud-Hooks
-----------------
  
  - Twitter_ 

       Commit Messages auf Twitter posten.

  - TravisCI_ 

        ``make && make test``

  - ReadTheDocs_ 

        Generierung von Dokumentation.

  - Bugzilla_ 

        Linking von Bugs in Commit Message.

  - Email_

        Bei Commit Email an Mailingliste schicken.

.. _Twitter: https://twitter.com/cloudkittens
.. _TravisCI: https://travis-ci.org
.. _ReadTheDocs: https://readthedocs.org/
.. _Bugzilla: http://bugzilla.org
.. _Email: http://de.wikipedia.org/wiki/E-Mail
