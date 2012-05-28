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