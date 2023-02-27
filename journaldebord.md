# Projet table tactile : Journal de bord

## 16/01/2023
* Organisation du groupe
* Rédaction du cahier des charges
* Récupération du projet SeriousGame
* Récupération des équipemetns(3 tables )
    * démonter et réparer les connectiques, les tables en général.
    * constatation de la dégradation d'une partie d'une dernière table.
* Création d'un trello pour le projet
* Création Journal de bord

## 23/01/2023

Noah BOMPARD : 
- Mails a la responsable, du fablab, relance du fablab
- mail au contact informatique du crous 
- Inventaire des fichiers présents sur les tables tactiles 
- test tacticité de la table tactile avec vincent 
- début de la réinstallation linux, avec prise en charge tactile : https://codimd.math.cnrs.fr/YgER1zQEQiGpUR5LmfjqrA?both
- démontage et analyse du prblème de pile CMOS, mail de commande de la pile.
- j'ai commencé a apprendre a utiliser node.js en vue de l'application client/restaurant
- démontage des boitiers de commande pour les mettre a jour et les réparer a la maison (batterie CMOS à changer)
- tests avec ubuntu touch

Fikret KÜRKLÜ: 

- Recherche de données pour l'intégration d'informations liés à ADE, pour cela on va faire une exportation des données sous format ics pour ensuite les traités en javascript. Recherche de librairies pour traiter les données, je vais réaliser quelques essais avec ical.js, une librairie de chez Mozilla.Je vais lire la documentation. 
- Pour intégrer les menu du jours au sein du site web, deux choix s'offre à nous, faire du scrapping de la page des restaurants de chaque resto crous et réaliser un affichage sur notre appli, ce qui permettra facilement aux utilisateurs d'accéder au menu, ou bien contacter des membres du crous pour voir comment on pourrait accéder aux données plus facilement. Je pense réaliser un petit script python sous format de serveur web, qui réalisera de la récolte de données depuis lien fournis.
- J'ai également commencer à regarder quelques tutoriels three.js pour essayer une implémentation dans  la présentation de polytech que nous souhaitons réaliser.

Vincent Ducros:

- Création d'une extension gnome utilisant du javascript pour lancer un script bash avec une commande xrandr pour faire une rotation de l'écran.
- Vérification des capacités multipoints des tables : visiblement absentes. J'ai cherché sur Internet mais pas trouvé beaucoup d'informations même si visiblement c'était pas très bien supporté sur les versions un peu plus anciennes d'ubuntu installé actuellement.
- Aide à démonter et vérifier l'état des installs avec Noah

Benjamin Bracquier:
- vérification de l'existence du serveur local(il n'y en a pas)
- recherche d'information sur le changement en mode kiosk et si il faut changer de naviguateur internet
- -recherche d'information de la construction et structure de notre page d'acceuil

## 29/01/2023

Benjamin Bracquier:
- continue l'implémentation de la page d'acceuil avec ajout du carouselle
- déjà implémenter dans la page d'acceuil:météo,horloge(date),flux rss (le monde),lien vers le site de polytech
- recherche de jeu à porter pour qu'on y accède à partir de la page d'acceuil

Fikret KÜRKLÜ:
- Mise en place du projet web en générant un projet sous next js accompagné de tailwind
- Mise en place d'un calendrier ade avec FullCalendar
- Cherche une solution de convertir les documents json récupérer depuis le fichier ics d'ade sous un format spécifique.

Vincent DUCROS:
- Vérification de l'état de la table basse : l'écran n'est pas calibré
- Recherche sur comment calibrer des écrans tactiles
- Début de l'écriture de la documentation sur la création d'une extension GNOME Shell

Noah BOMPARD : 
- Recherches sur la mise en place d'un syst tactile ( ubuntu touch, touché, touchgg)
- réparation et mise en marche de la table basse
- début de l'écriture d'un script de démarrage pour mettre le mode kiosk au startup
- mise a jour des 5 machines vers ubuntu 22.04 ( inventaire, maj, compatibilité, etc...)


## 06/02/2023

Vincent Ducros:
- Fin de la documentation sur les extensions GNOME Shell
- Recherche sur la possibilité de lancer des applications installés localement sur un pc depuis un navigateur (pour lancer des jeux installés localement malgré le mode kiosque)

Noah BOMPARD : 
- Documentation sur la mise a jour ubuntu, le mode tactile, touché
- mise en place du script pour lancer le mode kiosk au startup avec gnome startup application
- fin des mise a niveau des ordis, ubuntu, multitouch, tactiles, et clic droit si appui long.

## 20/02/2023

Vincent Ducros:
- Setup complet d'une table pour la démonstration de la JPO
    + Mise en place du serveur local apache avec Benjamin
    + Importation et test du script de rotation sur la table : problème = on a bien la rotation de l'écran mais pas du digitizer
    + Remontage de la table et vérification de son bon fonctionnement
- Calibration de l'écran via xinput_calibrator

Fikret Kürklü:
- Récupération des données depuis ADE et conversion en json grâce à l'outil ical2json récupérer depuis NPM
- Début de la page EDT pour l'affichage des données récolté depuis ADE 

## 27/02/2023

Fikret KÜRKLÜ:
- Finalisation de la page ADE, et affichage des emplois du temps de trois formations : INFO, IESE, TIS
