# Documentation mode kiosk au démarrage

## but 
Le but de la table tactile, dans une démarche de fonctionnement dans un café, un espace public, la table doit être dans un mode "safe" un mode sécurisé qui ne laisse que ce que l'on décide visible et interactif.
### principe 
Nous devons d'abord créer notre script. Une fois le script créé, nous le copions et le collons dans le dossier / Etc / init.d (pour ce faire, nous devons être des utilisateurs root). Une fois que nous avons collé ce script, nous devons donnez-leur les autorisations pour exécuter ce fichier. Cela se fait en ouvrant un terminal dans le dossier et en tapant ce qui suit:


```bash=
chmod +x mi-script.sh
```
Maintenant, nous avons le script prêt et nous devons seulement dire au système de lire et d'exécuter le script que nous avons inséré dans le dossier, pour cela, nous exécutons la commande suivante dans le terminal:


```bash=
update-rc.d mi-script.sh defaults 80
```
Cela fera le système inclut un script au démarrage du système et avec chaque utilisateur qui est dans ce système, peu importe qu'il s'agisse d'un administrateur système ou d'un simple utilisateur. 
## solution utilisée
En s'inspirant du mode kiosk utilisé dans des entreprises qui doivent laisser un accès aux utilisateur "relativement surveillé" (fnac, darty, etc...) on décide de faire le même choix.

Pour lancer le mode kiosk dans un navigateur (ici firefox, car relativement partout, et sûr) on exécute la commande
```bash=
firefox --kiosk
```


## Solution basique - script au démarrage
Notre première solution, est de créer un simple scrpit.sh qui contient la commande ci dessus, et de l'exécuter au démarrage.

le problème est la dangerosité de cette idée, même si elle marche et qu'on l'a déja utilisée, on doit modifier des fichiers systèmes, et ce n'est que après l'ouverture de la session que les logiciels marchent, donc lancer un script avant l'initialisation de la session n'est pas considéré comme sécurisé et un bonne idée, surtout qu'il y a une meilleure solution

## Solution optimisée - script au lancement de la session

Il existe depuis peu, une optimisation crée par gnome qui permet d'activer un menu "applications au démarrage"
en effectuant ces commandes : 

```bash=
sudo apt-get update -y
sudo apt-get install -y gnome-startup-applications
```
on obtient dans le menu de services (en bas à gauche) une application "applications au démarrage" dans laquelle il est possible de séléctionner un ensemble d'actions a effectuer au démarrage ( donc également des commandes uniques)

Il suffit d'ajouter une entrée avec la commande pour le mode kiosk de firefox, et voila ! pas besoin de script, de modifier les fichiers systèmes, et l'application, développée par gnome est sure et soutenue.





