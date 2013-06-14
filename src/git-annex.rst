.. _git_annex:

=============================
Git Annex: Dropbox fuer Harte
=============================

.. figure:: /_static/gitcloud.png
   :class: fill

---------------------------------
``git annex`` - Dropbox for geeks
---------------------------------
|

.. image:: /_static/gylfie.png
   :align: center
   :width: 400px


----------------------
Was ist ``git-annex?``
----------------------

**Problem:**

    * Git eignet sich aufgrund seiner Funktionsweise nur bedingt für große
      Dateien
    * Großen Dateien → hoher Ressourcenverbrauch

**Abhilfe: annex**
    
    * Ein Wrapper um ``git`` herum, der git *,,aufbohrt''*
    * Nur Metadaten werden verwaltet 
    * Content wird nicht *,,getrackt''*, git Features weiterhin vorhanden


------------------------------
Wie funktioniert das Ganze? #1
------------------------------

**Repository anlegen**

.. code-block:: bash

    $ mkdir annex
    $ cd annex
    $ git init .
    Initialized empty Git repository in /home/christoph/annex/.git/
    
    $ git annex init 'repo on desktop'
    init repo on desktop ok
    (Recording state in git...)


**Files hinzufügen**

.. code-block:: bash

    $ cp ~/debian-7.0.0-amd64-netinst.iso .
    $ git annex add .
    add debian-7.0.0-amd64-netinst.iso (checksum...) ok
    add wallpaper-279066f0.jpg (checksum...) ok
    (Recording state in git...)

------------------------------
Wie funktioniert das Ganze? #2
------------------------------

**Dateien commiten.** 
    
.. code-block:: bash

    $ git commit -am 'files added.'
    [master (root-commit) 1dcad58] files added.
    2 files changed, 2 insertions(+)
    create mode 120000 debian-7.0.0-amd64-netinst.iso
    create mode 120000 wallpaper-279066f0.jpg

Und nun? Let's sync! 


------------------------------
Wie funktioniert das Ganze? #3
------------------------------

**Dateien synchronisieren**
    
.. code-block:: bash

    $ git clone /home/christoph/annex/
    Cloning into 'annex'...
    done.
    
    $ cd annex 
    $ ls
    debian-7.0.0-amd64-netinst.iso  wallpaper-279066f0.jpg
    $ feh wallpaper-279066f0.jpg
    feh WARNING: wallpaper-279066f0.jpg does not exist - skipping
    feh: No loadable images specified.
    See 'feh --help' or 'man feh' for detailed usage information
        
    $ git annex get wallpaper-279066f0.jpg
    get wallpaper-279066f0.jpg (merging origin/git-annex into git-annex...)
    (Recording state in git...)
    (from origin...) ok
    (Recording state in git...)


----------------------
``git annex`` Features
----------------------

    * Location Tracking
    * Future Proofing
    * Backup Copies
    * Special Remotes
    * Transfering Data
    * Distributed Version Control

.. image:: /_static/annex.png
   :align: center
   :width: 200px

-----------
Alles okay?
-----------

**njaaaa**
    
    * Noch recht stark in der Entwicklung
    * Im Moment hauptsächlich was für Geeks
    
**Aber**

    * Abhilfe in Arbeit →  Webfrontend


------------------------------------------------
Warum überhaupt das Ganze, es gibt doch Dropbox?
------------------------------------------------

**Interessante Features die es bisher so nicht gibt:**

    * Verschiedene *,,cloud remotes''* nutzbar z.B. ``box.com``, ``rsync.net``, ``Amazon S3``
    * Kontrolle liegt beim Benutzer, nicht Storage Anbieter - interessant für
      Unternehmen mit kritischen Daten.
    * Verschlüsselung, Vertrauensstufen, Sharing etc.
    * Verschiedene ,,Repository Groups'' definierbar und kombinierbar → 
      verschiedene Szenarien abdeckbar.
    * Praktisch viele Features die man von einer gutem Storage-Lösung erwartet


--------------------------------
Power of git-annex for everybody
--------------------------------

|
|
|
|
|
|

.. raw:: html

    <center><b>Frontend Demo + <a href="http://downloads.kitenet.net/videos/git-annex/git-annex-xmpp-pairing.ogv">Dropbox usage Video</a></b></center>

|
|

.. image:: /_static/annex.png
   :align: center
   :width: 200px

------------------------------
Nun zum Kernthema des Vortrags
------------------------------

|
|
|
|
|

Code Hosting mit Github: :ref:`github`
