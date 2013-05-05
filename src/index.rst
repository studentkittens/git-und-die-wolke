=================
Git und die Wolke
=================

.. figure:: /_static/gitcloud.png
   :class: fill

Begriffserklärung
-----------------

.. rst-class:: build

- **git** - Ein dezentrales Versionsverwaltungssystem.
- **und** - Ein deutsches Bindewort.
- **die** - Ein deutscher Artikel.
- **Wolke** - Das worum es in dieser Vorlesung geht.

|
|
|

.. rst-class:: build

- →	 Wie man die Cloud für seinen Code nutzt.
- →	 Ein Drama in 4 Akten.

Git-Basics
----------

.. rst-class:: build

- Vorurteile:

  - *Ich bin doch nur ein einzelner Entwickler!*
  - *Ist doch total oversized!*
  - *Wann schau ich schon alte Versionen an?*
  - *Ich hab doch Dropbox!*

|
|

.. rst-class:: build

- Dezentral vs. Zentral.
- Einführung in die ``git shell``.
- Workflows, Branches, Repository, Visualisierung.

Git als Storage Service
-----------------------

|
|
|

.. rst-class:: build

- Git-annex - git als ``Dropbox`` nutzen
- Verschiedene Backends möglich 
  
  - **Amazon S3 Cloud Storage**
  - **XMPP**
  - **WebDAV**

Github
------


.. rst-class:: build

- Platzhirsch in Punkto Code-Hosting
- Freie Repository für Open-Source Projekte.
- Integration in andere Cloud-Dienste via ``git hooks``:

  - **ReadTheDocs**
  - **TravisCI**
  - **Twitter ☺**
  - **etc.**

Übung
-----

|
|
|


.. rst-class:: build

- Wird eine Überraschung ☺
- (LEDs are possible)
- Gitosis kommt auch vor.




.....


Zeitplan
--------

- Zeitplan aufzeigen
- Git Cheat-Sheet austeilen


ca 60 Min
---------

- Kurze Personenvorstellung
- Was ist git?

    - Ein Versionsverwaltungssystem
    - Ein Protokoll
    - Ein Filesystem

- Warum haben wir etwas zu git zu sagen?

    - "Sollte jeder Informatiker mal gehört haben!""

- Spielzeug auspacken

Basic - Befehle:

    - git init / clone                            - Begriff: Repository
    - git add / git commit                        - Begriff: Commit, Staging Index, Working Tree
    - git show / git diff                         - Begriff: Diff
    - Erklärung der Objektdatenbank mit Spielzeug, tree .git
    - git branch/merge / git checkout / git tag   - Begriff: Branches u. Tags
    - git push / git pull / git remote            - Begriff:

- git cheatsheet austeilen.

Hardcore - Befehle:

Befehle:

http://s3-ec.buzzfed.com/static/enhanced/terminal05/2012/4/27/11/enhanced-buzz-17410-1335541412-3.jpg
http://s3-ec.buzzfed.com/static/enhanced/terminal05/2012/4/27/12/enhanced-buzz-17759-1335543295-26.jpg
http://www.beefjam.com/images/2330.jpg


    - git stash
    - git rebase - Erklärung mit Spielzeug
    - git bisect - Nicht nach 'bisection' bei google bilder suchen
    - git oberfläche zeigen


(Puffer falls wir früher fertig werden - back to diz.)


ca 15 Min (50 Min)
------------------

Kitteh:

- git annex:

    - WebGUI 

- Kurzer Ausblick -> Git als Speicherdienst


70 Min (65 Min)
---------------

- Github -> Git in der Wolke (Github GUi Client)
- Kitteh: Infrastructure as a Service
- Fork, Pull Requests, Metriken
- Github hooks
  - Buildhook
  - TravisCI
  - ReadTheDocs
  - Twitter
  - Bugzilla
  - Metriken 
  - Email-Hook
- Github API 
- Gist
- Workflows
- 15 Min Pause

30 Min (Praxisübungen und Fragestunde)
--------------------------------------
- Github Organisation -> Konten anlegen -> pushen -> Raspberry leuchtet
- Mit einer Hochschulkonformen-Sprache Beispielprojekt -> MakeTest -> Ampel ->
  Email an Projektleiter Schaible
 Mit gource git repo visualisieren.
