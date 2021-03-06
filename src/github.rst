.. _github:

=======================
Github: Ab in die Wolke
=======================

.. figure:: /_static/gitcloud.png
   :class: fill

---------------
Was ist Github?
---------------

.. rst-class:: build

- Ein (Social-)Code-Hosting Dienst.
- Statistiken:

    - ~3,5 Millionen User 
    - 6 Millionen Repositories
    - 158 Mitarbeiter
    - April 2008 mit 6000 Usern und 2500 Repos gestartet.

- Bekannte Projekte:

    - Erlang, PHP, Perl, Clojure
    - Mirros: Linux-Kernel, Ruby
    - Git itself
    
-------
Octocat
-------

.. image:: /_static/octocat.jpg
    :align: center
    :width: 80%


----------------
Was kann Github?
----------------

.. rst-class:: build

- Für Open-Source kostenlos.

   - Einschränkungen: 1 GB Speicherplatz.

- Infrastructure as a Service
- Für Unternehmen gibt es ``private repos``.
- Für große Unternehmen kann man die Github-Software lizenzieren.
- Eigener Pastebin mit Versionierung ``Gist``.
- Volltextsuche über alle Repositories.


Demo: Nutzerprofil
------------------

- Git kennt nur den Namen und Email des Nutzers.

.. code-block:: bash

    # Wird in ~/.gitconfig gespeichert
    $ git config --global user.name "John Doe"
    $ git config --global user.email johndoe@example.com

- GitHub kennt unabhängig davon noch einen Account.
- Diesem sind ``1..n`` Repository zugeordnet. 
- Zudem kann dieser User andere Projekte Forken, Bug-Reports schreiben u.v.m.


Demo: Fork
----------

- Ein Fork ist ein ``git clone`` mit anderen Namen.
- Man klont ``alice/example.git`` zu ``bob/example.git``.
- Dann macht man den Code den man geforkt hat kaputt.
- Wenn man fertig (mit der Welt) ist kommt ein **Pull Request**.

Demo: Pull Requests
-------------------

Ablauf ohne GitHub:

.. code-block:: bash

    # Auf Seite des Forkers (bob)
    $ git request-pull HEAD^1 https://github.com/<bob>/repo.git 
    The following changes since commit 04ca9db3149956ed7670d699cb4b4328386b88e1:
      Sophisticated commit message. (2013-05-11 00:36:56 +0200)
    are available in the git repository at:
      https://github.com/<bob>/repo.git master
    $ git push
    # Bob sendet diesen Text an Alice
    # Auf Seite des Annehmers (alice):
    $ git remote add bob https://github.com/<bob>/repo.git
    $ git pull bob 04ca9d

Ablauf mit GitHub:

    - ``bob`` macht über GitHub einen Pull Request.
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

Code lässt sich online:

  - Browsen_.
  - Blamen_.
  - Historisch_ betrachten.
  - Editieren_.

.. _Browsen: https://github.com/studentkittens/git-demo/blob/master/Makefile
.. _Blamen: https://github.com/studentkittens/git-demo/blame/master/Makefile
.. _Historisch: https://github.com/studentkittens/git-demo/commits/master/Makefile
.. _Editieren: https://github.com/studentkittens/git-demo/edit/master/Makefile

|
|
|
|
|

**Tipp:** Auch Bilder, Dokumente und Videos sind previewbar.

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

.. _Beispiel: https://github.com/sahib/glyr/contributors
.. _Bugtracker: https://github.com/sahib/glyr/issues
.. _Downloads: https://github.com/sahib/glyr/tags

Demo: Sonstiges #2
------------------

- **Wiki/Webpagehosting:**

    - Leicht erstellbares wiki.
    - ``gh-pages`` branch wird unter ``<user>.github.io/<repo>`` gehosted.
    - Beispiel: http://sahib.github.io/rmlint/

- **Soziales:**

    - Andere User kann man ``followen``. 
    - Andere Repos kann man ``watchen``.
    - Anzeige von Aktivitäten anderer auf dem Dashboard_.

.. _Dashboard: https://github.com/

----------
Github-API
----------

Möglichkeit um…

.. rst-class:: build

- …GitHub in Anwendungen zu integrieren.
- …Volltextsuche auf allen Repositories.
- …Statisten.
- …Activities. (Alternative zu ``git hooks``)
- …Aktionen zu triggern (z.B. Pull Request).

.. code-block:: bash

    # Alle Repositories eines Users auflisten
    $ curl -q https://api.github.com/users/qitta/repos \
      | grep 'full_name'
    "full_name": "qitta/dotfiles",
    "full_name": "qitta/foozel",
    "full_name": "qitta/scripts",


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

       Commit-Messages auf Twitter posten.

  - TravisCI_ 

        ``make && make test``

  - ReadTheDocs_ 

        Generierung von Dokumentation.

  - Bugzilla_ 

        Linking von Bugs in Commit-Message.

  - Email_

        Bei Commit Email an Mailingliste schicken.

.. _Twitter: https://twitter.com/cloudkittens
.. _TravisCI: https://travis-ci.org
.. _ReadTheDocs: https://git-python-project.readthedocs.org/en/latest/
.. _Bugzilla: http://bugzilla.org
.. _Email: http://de.wikipedia.org/wiki/E-Mail

-------------------------
Meine Damen und Herren...
-------------------------

|
|
|
|
|

Die Haupattraktion des Tages: :ref:`git_uebung`
