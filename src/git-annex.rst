=============================
Git Annex: Dropbox fuer Harte
=============================

.. figure:: /_static/gitcloud.png
   :class: fill

--------------------------------
git annex - a wrapper around git
--------------------------------
|

.. image:: /_static/gylfie.png
   :align: center
   :width: 400px


------------------
Was ist git-annex?
------------------

**Problem:**

    * Git eignet sich aufgrund seiner Funktionsweise nur bedingt für große
      Dateien
    * Großen Dateien → hoher Ressourcenverbrauch

.. image:: /_static/annex.png
   :align: center
   :width: 200px

------------------
Was ist git-annex?
------------------

**Abhilfe: annex**
    
    * Ein wrapper um git herum, der git ,,aufbohrt''
    * Nur Metadaten werden verwaltet 
    * Content wird nicht ,,getrackt'', dennoch sind git features für das
      Filemanagement weiterhin verfügbar und ,,nice''


.. image:: /_static/annex.png
   :align: center
   :width: 200px
    
------------------
git annex features
------------------

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
    * Im moment hauptsächlich was für Geeks
    
**Aber**

    * Abhilfe in Arbeit →  Webfrontend


-------------------------------------------
Warum überhaupt das Ganze, es gibt Dropbox?
-------------------------------------------

**Interessante Features die es bisher so nicht gibt**

    * Verschiedene ,,cloud remotes'' nutzbar z.B. Box.com, Rsync.net, Amazon S3
    * Kontrolle liegt beim Benutzer, nicht Storage anbieter - interessant für
      unternehmen mit kritischen Daten.
    * verschlüsselung, Vertrauensstufen, Sharing etc.
    * verschiedene ,,Repository Groups'' definierbar und kombinierbar → 
      verschiedene Szenarien abdeckbar.
    * Praktisch viele Features die man von einer gutem storagelösung erwartet


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

    <center><b>Frontend Demo + Dropbox usage video</b></center>

|
|

.. image:: /_static/annex.png
   :align: center
   :width: 200px
