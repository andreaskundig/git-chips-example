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

