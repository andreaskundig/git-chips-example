Garder un historique
====================
création d'un projet
--------------------
mkdir chips  
cd chips  

premier fichier chips.html
--------------------------
git status  
git init --> configuration  
git status --> untracked  
git add chips.html  
git commit -m 'commit message: i can haz cheeseburger'
git log  
gitk  

deuxieme fichier chips.css
--------------------------
modification de chips.html  
git add chips.css chips.html  
git commit -m 'deux fichiers'  

se promener dans l'histoire
--------------------------
git log  
git checkout (premier commit) --> un seul fichier  
git checkout (deuxieme commit) --> deux fichiers  
git checkout master --> il faut être sur une branche pour travailler  

faire un peu d'ordre
--------------------
mv chips.html index.html --> fichier renommé  
git status  
git rm chips.html  
git add index.html  
mkdir css  
git mv chips.css css --> fichier déplacé  
git status --> les changements sont dans l'index  
changer le lien vers chips.css dans index.html  
git status --> index.html à la fois dans index et modified  
git add index.html  
git log index.html --> ou sont passés les commits de chips.html?  
git log --follow index.html --> histoire reconstituée  
git log --stat --follow index.html --> voir le renommage  
git log -p -2 --follow index.html --> détail des deux précédents commits 

Branches
========

étant satisfait de ce site, on le met en ligne
master représente la version en ligne
le développement continue sur une branche

issue 53: une vraie recette
---------------------------
le développement continue sur une branche  
git branch iss53 --> branche créée  
git checkout iss53  --> aller sur la branche  
ajouter des couleurs à chips.css  
git commit -am 'C3: une vraie recette' --> add et commit simultanément  

bug à réparer en production
---------------------------
git checkout master  
git checkout -b hotfix1 --> créer la branche et travailler dessus
ajouter un espace dans index.html  
git commit -a -m 'C4: un espace'  

intégrer hotfix1 en production
------------------------------
git checkout master  
git merge hotfix1  
git branch -d hotfix1 --> effacer la branche

issue 54: plus appétissant
--------------------------
git checkout -b iss54
changer la couleur, ajouter du texte
git commit -am 'C6: plus appetissant'

hotfix2: plus appétissant tout de suite
---------------------------------------
git checkout master
git checkout -b hotfix2
changer le texte
git commit -am 'C7: plus appetissant tout de suite'

hotfix2 appliqué à master
-------------------------
git checkout master
git merge hotfix2

iss54 appliqué à master
-----------------------
git merge iss54 --> conflit
corriger index.html
git commit -am 'C8: merge manuel apres le conflit'

Hébergement sur internet
========================
Créer un compte sur bitbucket.org
---------------------------------
Create new repository  
choisir un nom  
Cocher git comme 'repository type'  

retourner dans la ligne de commande:
------------------------------------
git remote add origin https://bitbucket.org/kundig2/chips-example.git  
git push -u origin master  

donner l'accès à un autre développeur (B)
-----------------------------------------
admin, access management, ajouter un nom, write  

B reprend le projet chez lui
----------------------------
mkdir chips2  
cd chips2  
git clone https://bitbucket.org/kundig2/chips-example.git chips3  

A fait des modifications
------------------------
éditer un fichier  
git push  

B fait aussi des modifications
-------------------------------
git push origin master --> rejeté  
git fetch origin master  
git merge origin/master --> conflits  
réparer les conflits  
git commit -am 'merge'  
