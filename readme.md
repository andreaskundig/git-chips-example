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
