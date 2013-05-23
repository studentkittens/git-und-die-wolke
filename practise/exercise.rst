Übungsaufgaben: Git und die Wolke
=================================

Einleitung
----------
    
Um das gerade Erlebte verinnerlichen zu können, habt ihr nun eine halbe Stunde
Zeit euch mit ``git`` und ``Github`` vertraut zu machen. Nach dem erfolgreichen Ableben
der Prüfung gibt es für jeden von Euch eine kleine Überraschung.


I - Git lokal
-------------

Auch wenn es in erster Linie nichts mit ,,der Cloud'' zu tun hat, sind wir der
Meinung dass es jeder Informatiker mal gehört haben sollte, es geht um git. Um
es nutzen zu können brauchen wir ein *Repository*.

In der ersten Übunggeht es nun darum ein Repository anzulegen und sich mit dem ``git``-Werkzeugen
vertraut zu machen.

    Folgende Schritte sind mit Hilfe des Cheatsheets durchzuführen:

        * Konfiguriere deine ``git`` "Identität".
        * Lege einen Ordner an und Initialisiere ein neues Git Repository
        * Lege eine neue README Datei an, fülle sie mit Text und mach sie dem git
          Repository bekannt
        * Lege eine **.gitignore** Datei in deinem Repository an welche alle
          Dateien mit der Endung **.bin** und den Ordner **test** ausschließt,
          teste deine Konfiguration: **git status**
        * Füge weitere Dateien deinem Repository hinzu und committe diese mit
          entsprechend aussagekräftigen Messages -> Prüfe deine git History mit
          ``gitg``, ``tig``, ``git log`` oder ``gitk``.
        * Als nächstes soll ein Branch namens **katzenbaum** angelegt werden, in
          diesem Branch sollen nun zwei Dateien abgeändert werden und eine Neue
          hinzugefügt werden, anschließen ist dieser Branch mit dem Master
          Branch zu mergen. 

          Forgeschrittene können auch ``git rebase`` nutzen!


II - Über den Wolken…
---------------------

In dieser Übung geht es darum Github als ,,Cloudservice'' nutzen zu lernen. Als
Grundvoraussetzung brauchen wir hierfür einen Github Account und bitte euch
hiermit sich einen z.B. mit der ``hof-university.de``-Adresse anzulegen (dieser
Account kann nach der Übung wieder gelöscht werden).

    Folgende Teilaufgaben sind durchzuführen:

        * Richte dir einen Github Account unter https://www.github.com
        * Erstelle ein Repository mit einem beliebigen Namen auf Github 
        * Clone dein Repository, mach Änderungen analog zur lokalen Übung und
          Pushe deine Arbeit in die Wolke

        * Forke das Organisationsprojekt **xyz**
        * Führe ein paar Änderungen am Code durch (z.B. Kommentaränderungen)
        * ...und dann?

III - Zu Himbeeren pushen
-------------------------

Zu guter letzt.
