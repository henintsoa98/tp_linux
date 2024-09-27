# I - Afficher des informations du système
## 1 - Afficher dans le terminal la date du système
**Methode 1**
```bash
date
```
**Methode 2**
```bash
timedatectl
```

## 2 - Afficher les utilisateurs connectés au système
**Methode 1**
```bash
whoami
```
**Methode 2**
```bash
id -un
```

## 3 - Afficher le chemin absolu du dossier personnel utilisateur
```bash
pwd
```

# II - Naviguer dans le système
## 1 - Aller dans le répertoire bin du système et afficher son contenu
```bash
cd /bin
```
```bash
ls
```

## 2 - Revenir dans le dossier utilisateur
**Methode 1**
```bash
cd
```
**Methode 2**
```bash
cd ~
```
**Methode 3**
```bash
cd $HOME
```

# III - Création de fichier
## 1 - Créer un fichier hello.c contenant le code minimal d’un programme en langage C. Afficher le type de contenu de ce fichier
**Methode 1** : redirection + cat + EOF
```bash
cat > hello.c << EOF
#include <stdio.h>

int main ()
{
    printf ("Hello World");
    return 0;
}
EOF
```
**Methode 2** : redirection + echo , si vous utiliser " dans le code, vous devez utiliser \" parce que c'est le limiteur de fin et on doit l'echapper
```bash
echo "
#include <stdio.h>

int main ()
{
    printf (\"Hello World\");
    return 0;
}
" > hello2.c
```
**Methode 3** : editeur de texte
```bash
nano hello.c
```
```bash
vim hello.c # pour les pro
```
**Affichage du code**
```bash
cat hello.c
```
```bash
cat hello2.c
```

## 2 - Compiler le programme hello.c précédent et afficher le type de contenu de l’exécutable obtenu
```bash
gcc hello.c -o hello.x
```
```bash
file hello.c
```
```bash
./hello.x
```

## 3 - Dans votre dossier personnel, créer un fichier appelé mesMusiques. Insérer quelques lignes à l’intérieur de ce fichier à l’aide de votre éditeur de texte.
en utilisant nano : editer votre fichier, puis <ctrl+o> pour sauvegarder, et <ctrl+x> pour quiter, utiliser <enter> si validation requises
```bash
touch mesMusiques
```
```bash
nano mesMusiques
```

## 4 - Afficher le contenu du fichier mesMusiques sur le terminal
```bash
cat mesMusiques
```

## 5 - Afficher le type de contenu du fichier mesMusiques sur le terminal
```bash
file mesMusiques
```

## 6 - Quelle est la taille du fichier mesMusiques (plusieurs manières pour l’afficher) ?
**methode 1** : taille du fichier en octets sur la 5eme colonne
```bash
ls -l mesMusiques 
```
**methode 2** : taille en o, Ko, Mo, Go ...
```bash
ls -lh mesMusiques
```

# IV - Copie et deplacement
## 1 - Effectuer une copie du fichier mesMusiques vers le fichier myMusic.
```bash
cp mesMusiques myMusic
```

## 2 - Afficher la taille des 2 fichiers et comparer
```bash
ls -l myMusic mesMusiques
```

## 3 - Renommer le fichier myMusic en mySongs
```bash
mv myMusic mySong
```

## 4 - Quelle différence entre les commandes mv myMusic mySongs et cp myMusic mySongs ?
mv pour renommer et cp pour copier

# V - Création de dossiers
## 1 - Créer un dossier myFiles
```bash
mkdir myFiles
```

## 2 - Déplacer le fichier mySongs dans le dossier myFiles, et le renommer en songs2 (tout ça en une seule commande).
```bash
cp mySong myFiles/song2
```

## 3 - Créer 2 sous-dossiers à myFiles : Albums/favorites/ et Artistes/ (sans se déplacer dans myFiles). Pour le sous-répertoire favorites, il faut le créer en une seule commande)
**Methode 1**
```bash
mkdir -p myFiles/Albums/favorites/ myFiles/Artistes
```
**Methode 2**
```bash
mkdir -p myFiles/{Albums/favorites,Artistes}
```

# VI - Affichage de fichiers/dossiers
## 1 - Décrire ce que fait la commande ls -l ?
lister les dossier et fichier avec les details

## 2 - Afficher le contenu détaillé du dossier myFiles (même les fichiers cachés)
```bash
ls -la myFiles
```

## 3 - En plus de l’affichage précédent, afficher les numéros des inodes
```
ls -lai myfiles
```

## 4 - Lister les fichiers du dossier courant en affichant les numéros des inodes. Comparer le numéro du dossier myFiles avec le numéro du dossier "." de la question précédente
```bash
ls -lai .
ls -laiR
```

## 5 - A quoi sert l’option -R de la commande ls ?
lister le dossier actuel ou le dossier en parametre et lister les sous-dosssier recursivement
```bash
ls -R
```

## 6 - Quel est l’ordre par défaut d’affichage des éléments suite à la commande ls ?
Ordre alphabetique
```bash
ls -l
```

## 7 - Quelles sont la(les) option(s) de la commande ls qui permettent de modifier l’ordre d’affichage ?
**L'option -l pour voir le resulat par ligne, les commandes de triages sont :** \
Size
```bash
ls -lS
```
Time
```bash
ls -lSt
```
Extension
```bash
ls -lSX
```
-r permet de reverse de l'order des commandes precedente
```bash
ls -r
```
```bash
ls -lStr
```
```bash
ls -lSXr
```
```bash
ls -lSr
```


## 8 - Afficher le contenu du répertoire utilisateur en faisant apparaitre les fichiers les plus récemment utilisés en premier.
```bash
ls -lSt
```
# 9 - Comment afficher les droits d’accès d’un répertoire ?
```bash
ls -ld
```
```bash
ls -ld myFiles
```

# VII - Suppression de fichiers/dossiers
## 1 - Supprimer le répertoire myFiles à l’aide de la commande rm. Quel est le résultat ?
```bash
rm myFiles
```
on ne peut pas supprimer un repertoire avec rm
## 2 - Supprimer myFiles à l’aide de la commande rmdir. Quel est le résultat ?
```bash
rmdir myFiles
```
on ne peut pas supprimer un repertoire non vide
## 3 - Supprimer le dossier myFiles et tout ce qu’il contient avec la commande rm en mode récursif.
```bash
rm -r myFiles
```
## 4 - Maintenant que myFiles n’existe plus, relancer la commande précédente. Quel est le résultat ?
```bash
rm -r myFiles
```
on ne peut pas supprimer un repertoire non existan
## 5 - Relancer la commande précédente en faisant en sorte qu’elle n’affiche aucun message d’erreur si la cible n’existe pas.
```bash
rm -rf myFiles
```

# VIII - Droits d’accès
## 1 - Un répertoire a les droits suivants : drwx-x-x. Un utilisateur qui n’est pas le propriétaire peut-il afficher le contenu du répertoire ? Quelles sont les actions que peut faire cet utilisateur ?
Il ne peut pas afficher parce que pas de d : directory rwx : pour Proprietaire --x : pour meme Groupe --x pour autre \
Autre : pas de r : read \
Il peut selement entrer dans ce repertoire : -x

## 2 - Créer un dossier Moi, et affecter les droits suivants : drwxr-x-wx. Ces droits sont-ils pertinents pour un fichier ou un dossier ? Justifier. Proposer un cas général de droits restrictifs en fonction des utilisateurs. Modifier les droits du dossier avec votre proposition
```bash
mkdir moi
```
```bash
chmod 753 moi
```
```bash
ls -l
```
Ces droit sont pertinant pour les fichier, car on peut utiliser ce dossier pour (wx : write-execute), tout le monde peut ecrire ce qu'il veut, executer des commandes sur les fichers si il connait son nom, mais pas lister ces fichiers, car les autres le peuveut pas le lire que contient ce dossier \
Une droit restrictifs general est : drwxr-xr-x (755) parce que tout le monde peut lire et executer des commandes comme cat cp, mais ne peut pas changer le contenu du repertoire sauf si il est le proprietaire
```bash
chmod 755 moi
# tenter d'experimenter avec d'autre utilisateurs (creer si non existant)
# su - autreUser
```

# X - Alias de commandes
# 1 - Qu’est-ce qu’un alias ?
Un alias est un raccourci de commande ou de commande avec argument
# 2 - Afficher tous les alias actuellement chargés dans la session de votre terminal. Décrire le résultat affiché. Quel est l’impact d’un alias sur une commande si les deux ont exactement la même syntaxe ?
```bash
alias -p
```
Il affiche une commande, avec son equivalent
# 3 - Dans le terminal, entrer la commande suivante : alias cd=’ls’. Utiliser la commande cd : que se passe-t-il ?
```bash
alias cd='ls'
```
```bash
cd
```
cd est devenue une commande comme ls
# 4 - Supprimer l’alias cd créé précédemment. Tester à nouveau la commande cd pour voir si le changement est bien pris en compte.
```bash
alias cd='cd'
cd
```
# 5 - Définir un alias myDirs qui va afficher tous les sous-répertoires de la racine de votre dossier personnel. Tester l’alias créé
```bash
alias myDirs='ls ~'
```
```bash
myDirs
```
# 6 - Quitter le terminal, et le réouvrir. Utiliser l’alias précédent : que se passe-t-il ?
L'alias n'est pas present sur ce nouvelle session
# 7 - Afficher le contenu du fichier .bashrc qui se trouve à la racine de votre répertoire personnel. Que contient ce fichier ?
```bash
cat ~/.bashrc
```
# 8 - Avec un éditeur de texte, modifier le fichier .bashrc pour y ajouter l’alias qui affiche les dossiers du répertoire personnel. Tester à nouveau l’alias myDirs dans la session actuelle du terminal. Que se passe-t-il ?
```bash
nano ~/.bashrc
```
ajouter alias myDirs='ls ~'
ou en un seul command
```bash
echo "alias myDirs='ls ~'" | tee -a ~/.bashrc
```
# 9 - Fermer le terminal et rouvrir une nouvelle session. Tester l’alias myDirs : que se passe-t-il ?
```bash
myDirs
```
Il afficher les dossier du repertoire personnel


# BASH CHEETSEET
```bash
ip a
```
## grep : filter les lignes
```bash
ip a | grep -i UP
```

## awk : filtrer les colonnes
colonne 2, 4 et 9. NB : les catacteres sont mis entre "" dans awk
```bash
ip a | grep -i up | awk '{print $2"}'
```
```bash
ip a | grep -i up | awk '{print $2" "$4" "$9}'
```
```bash
ip a | grep -i up | awk '{print $2" "$4" STATUS : "$9}'
```
Sauvegarder cette sortie dans un variable
```bash
FILTERED=$(ip a | grep -i up | awk '{print $2" "$4" STATUS : "$9}')
```
## sed : echanger des caracteres
UNWKOWN en Inconnue, UP en marche et DOWN en eteint
```bash
echo "$FILTERED"
```
```bash
echo "$FILTERED" | sed "s/UNKNOWN/Inconue/"
```
```bash
echo "$FILTERED" | sed "s/UNKNOWN/Inconue/;s#UP#marche#"
```
```bash
echo "$FILTERED" | sed "s/UNKNOWN/Inconue/;s#UP#marche#;s/DOWN/eteint/"
```
Sauvegarder cette sortie dans un variable
```bash
FILTERED2=$(echo "$FILTERED" | sed "s/UNKNOWN/Inconue/;s#UP#marche#;s/DOWN/eteint/")

```

## column : afficher en tableau
```bash
echo "$FILTERED" | sed "s/UNKNOWN/Inconue/;s#UP#marche#;s/DOWN/eteint/" | column -t
```
ou
```bash
echo "$FILTERED2" | column -t
```

Ce sont les PIPE, ils mettent a disposition du commande a droite les resultats du commandes a gauche
