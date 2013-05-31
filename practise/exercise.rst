=================================
Übungsaufgaben: Git und die Wolke
=================================

Motivationshilfe:
-----------------

    - Wer Aufgabe I fertig gemacht hat kriegt einen Octocat-Sticker.
    - Wer sich bei Aufgabe II hervortut bekommt auch eine kleine Überraschung.

Vorraussetzungen: 
-----------------

    Ihr habt aufgepasst, sonst keine. :-)
    Umgang mit der Shell ist aber hilfreich.

=============
I - Git Lokal
=============

Ein wenig lokales Warmup mit ``git``. (Dauer ca. 15 min.)

Folgende Schritte sind mit Hilfe des Cheatsheets durchzuführen:

    1) Lege einen Ordner an und Initialisiere ein neues Git Repository
    2) Schreibe eine neue ``README.txt`` Datei und füge sie dem ``Stage`` hinzu.
    3) Comitte deine Änderungen und schaue vorher und nacher nach mit ``git status`` nach was sich ändert hat. 
    4) Prüfe dein Vorgehen in eine Visualisierungstool deiner Wahl. (zb ``git log``)
    5) Lege ein ``.gitignore`` Datei an und exkludiere darin alle Files mit der
       Endung ``.txt``. Stell sicher dass es funktioniert hat. Wird ``README.txt`` ignoriert?
    6) **Branching:**
        
       1) Lege einen neuen Branch ``readme-improv`` an.
       2) Mach einen neuen commit, und verändere in diesem ``README.txt``
       3) Wechsel zum ``master`` branch.
       4) Mache auch dort einen Commit in dem du ``README.txt`` veränderst.
       5) Merge ``master`` mit ``readme-improv``!
          Forgeschrittene können hier auch ``git rebase`` nutzen.

|
|
|
|
|
|
|
|
|
|
|
|
|
|
|

=======================
II - Collaboration Game
=======================

Bei ``git`` geht es um Zusammenarbeit. Deshalb wollen wir einen Workflow
gemeinsam mal probieren.


    0) Bildet Gruppen von 2 - 3 Mann. Maximal 8 Gruppen.
    1) Legt euch einen GitHub-Account an. Ihr könnte ihn später auch wieder löschen.
    2) Teile ``git`` mit wer ihr seid (Tipp: Cheatsheet.)
    3) Hier findet ihr ein Python-Projekt das noch nicht ganz fehlerfrei ist:

        https://github.com/studentkittens/git-python-project.git

       Forkt dieses Projekt!
    4) Clont das geforkte Projekt in euere VM: 

       |

       .. code-block:: bash

            $ git clone https://github.com/<euer_user>/git-python-project.git
            $ cd git-python-project

    5) Wer hiermit fertig kriegt von uns einen Task (meldet euch!).

       Jeder Task besteht aus einer fehlerhaften Python Funktion. Eure Aufgabe
       ist es nun diese entweder durch Überlegung zu reparieren, oder unter
       Anwendung der vorgestellten git tools. Weitere Hinweise findet sich auch
       im Quelltext.

       Auf den Zettel den eine Gruppe bekommt steht der Name des Directories das
       ihr bearbeitet. Darin findet sich auch immer nur eine **.py** Datei mit
       der Aufgabe. Editiert diese.

    6) Wenn ihr fertig seid prüft hiermit nach ob der Test durchläuft:

       |
    
       .. code-block:: bash

               $ make test_<task_name>

       
    7) Falls ja: Pusht eueren Code zu eurem Fork.
    8) Macht ein Pull Request auf das Ursprungs Repository.
    9) Sollte alles gut gehen sollte die LED vorne von Rot nach Grün wandern.

       Je Nach Schwierigkeit der Aufgabe ein Stück mehr.


Der aktuelle Zustand eurer Arbeit wird durch eine LED am RaspberryPi farblich angezeigt: 

+------------+---------------------------------------+
| Rot        |  ``make test`` läuft nicht durch.     |
+------------+---------------------------------------+
| Gelb       | **RaspberyCI** buildet und testet.    |
+------------+---------------------------------------+
| Grün       | ``make test`` läuft erfolgreich durch |
+------------+---------------------------------------+


===========
III. Gource
===========

Keine Panik, Ihr müsst nichts machen.

Zum Abschluss visualisieren wir dann eure Arbeit!
