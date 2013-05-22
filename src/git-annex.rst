============================
Git Annex: Dropbox für Harte
============================

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

    * git eignet sich aufgrund seiner Funktionsweise nur bedingt für große
      Dateien
    * großen Dateien -> hoher Ressourcenverbrauch

.. image:: /_static/annex.png
   :align: center
   :width: 200px

------------------
Was ist git-annex?
------------------

**Abhilfe: annex**
    
    * ein wrapper um git herum, der git ,,aufbohrt''
    * nur Metadaten werden verwaltet 
    * Content wird nicht ,,getrackt'', dennoch sind git features für das
      Filemanagement weiterhin verfügbar und ,,nice''


.. image:: /_static/annex.png
   :align: center
   :width: 200px
    
------------------
git annex features
------------------

    * location tracking
    * future proofing
    * backup copies
    * special remotes
    * transfering data
    * distributed version control

.. image:: /_static/annex.png
   :align: center
   :width: 200px

-----------
Alles okay?
-----------

**nnnjjjjjjjjjaaaaa**
    
    * noch recht stark in der Entwicklung
    * im moment hauptsächlich was für geeks
    
**Aber**

    * Abhilfe in Arbeit -> Webfrontend


-------------------------------------------
Warum überhaupt das Ganze, es gibt Dropbox?
-------------------------------------------

**Interessante Features die es bisher so nicht gibt**

    * verschiedene ,,cloud remotes'' nutzbar z.B. Box.com, Rsync.net, Amazon S3
    * kontrolle liegt beim Benutzer, nicht Storage anbieter - interessant für
      Unternehmen mit kritischen Daten?
    * Verschlüsselung, Vertrauensstufen, Sharing etc.
    * Verschiedene ,,Repository Groups'' definierbar und kombinierbar ->
      verschiedene Szenarien abdeckbar 
    * praktisch viele Features die man von einer gutem storagelösung erwartet


---------------------------------
power of git annex for everybody?
---------------------------------

|
|
|
|
        ** Frontend Demo + Dropbox usage video **


.. image:: /_static/annex.png
   :align: center
   :width: 200px
