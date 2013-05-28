=================================
Übungsaufgaben: Git und die Wolke
=================================

Motivationshilfe:
-----------------

    - Wer Aufgabe I fertig gemacht hat kriegt einen Octocat-Sticker.
    - Wer sich bei Aufgabe II hervortut bekommt auch eine kleine Überraschung.

Vorraussetzungen: 
-----------------

    Ihr habt aufgepasst, sonst keine. 😃
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

==================
II - Collaboration
==================

    1) Legt euch einen GitHub-Account an. Ihr könnte ihn später auch wieder löschen.
    2) Teile ``git`` mit wer du bist.
    3) Hier findet ihr ein Python-Projekt das noch nicht ganz fertig ist:

        https://github.com/studentkittens/git-python-project.git

       Forkt dieses Projekt!
    4) Clont dieses Projekt in euere VM: 

       .. code-block:: bash

            $ git clone https://github.com/studentkittens/git-python-project.git
            $ cd git-python-project

    5) .. code-block:: python

        while time_left and tests_not_working:
            task = ask_staff_for_task()
            task.work_on_it()
            task.execute_tests()
            task.push_to_github()


Der aktuelle Zustand eurer Arbeit wird durch eine LED am RaspberryPi farblich angezeigt: 

+------------+------------+--------------------------+
| Rot        |  ``make test`` läuft nicht durch.     |
+------------+---------------------------------------+
| Gelb       | **TravisCI** buildet und testet.      |
+------------+---------------------------------------+
| Grün       | ``make test`` läuft erfolgreich durch |
+------------+---------------------------------------+
