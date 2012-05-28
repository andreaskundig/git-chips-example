Garder un historique
====================
cr�ation d'un projet
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
git checkout master --> il faut �tre sur une branche pour travailler  

faire un peu d'ordre
--------------------
mv chips.html index.html --> fichier renomm�  
git status  
git rm chips.html  
git add index.html  
mkdir css  
git mv chips.css css --> fichier d�plac�  
git status --> les changements sont dans l'index  
changer le lien vers chips.css dans index.html  
git status --> index.html � la fois dans index et modified  
git add index.html  
git log index.html --> ou sont pass�s les commits de chips.html?  
git log --follow index.html --> histoire reconstitu�e  
git log --stat --follow index.html --> voir le renommage  
git log -p -2 --follow index.html --> d�tail des deux pr�c�dents commits 

Branches
========

�tant satisfait de ce site, on le met en ligne
master repr�sente la version en ligne
le d�veloppement continue sur une branche

issue 53: une vraie recette
---------------------------
le d�veloppement continue sur une branche  
git branch iss53 --> branche cr��e  
git checkout iss53  --> aller sur la branche  
ajouter des couleurs � chips.css  
git commit -am 'C3: une vraie recette' --> add et commit simultan�ment  

bug � r�parer en production
---------------------------
git checkout master  
git checkout -b hotfix1 --> cr�er la branche et travailler dessus
ajouter un espace dans index.html  
git commit -a -m 'C4: un espace'  

int�grer hotfix1 en production
------------------------------
git checkout master  
git merge hotfix1  
git branch -d hotfix1 --> effacer la branche

issue 54: plus app�tissant
--------------------------
git checkout -b iss54
changer la couleur, ajouter du texte
git commit -am 'C6: plus appetissant'

hotfix2: plus app�tissant tout de suite
---------------------------------------
git checkout master
git checkout -b hotfix2
changer le texte
git commit -am 'C7: plus appetissant tout de suite'

hotfix2 appliqu� � master
-------------------------
git checkout master
git merge hotfix2

iss54 appliqu� � master
-----------------------
git merge iss54 --> conflit
corriger index.html
git commit -am 'C8: merge manuel apres le conflit'

H�bergement sur internet
========================
Cr�er un compte sur bitbucket.org
---------------------------------
Create new repository  
choisir un nom  
Cocher git comme 'repository type'  

retourner dans la ligne de commande:
------------------------------------
git remote add origin https://bitbucket.org/kundig2/chips-example.git  
git push -u origin master  

donner l'acc�s � un autre d�veloppeur (B)
-----------------------------------------
admin, access management, ajouter un nom, write  

B reprend le projet chez lui
----------------------------
mkdir chips2  
cd chips2  
git clone https://bitbucket.org/kundig2/chips-example.git chips3  

A fait des modifications
------------------------
�diter un fichier  
git push  

B fait aussi des modifications
-------------------------------
git push origin master --> rejet�  
git fetch origin master  
git merge origin/master --> conflits  
r�parer les conflits  
git commit -am 'merge'  
