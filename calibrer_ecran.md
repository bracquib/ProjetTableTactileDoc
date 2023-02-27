# Documentation : calibration d'un écran tactile sous Xorg

Certaines de nos tables tactiles n'étaient pas calibrées, ce qui rend leur utilisation plus compliqué car les boutons ne sont pas là ou l'utilisateur les attend.
Le processus de calibration est rendu très simple par l'utilisation de `xinput-calibrator` une application développée principalement par Tias Guns. L'avantage de ce programme est qu'il ne dépend pas d'un driver particulier (générique. Cependnant, il faut utiliser le système de fenêtrage Xorg puisque le programme va calibrer les valeurs de XInput directement.

## Installation et utilisation

1) Lancer `sudo apt install xinput-calibrator`.

2) Vérifier dans la page "A propos" que le système de fenêtrage utilisé est bien Xorg. Sur Ubuntu 22.04 (la version utilisée pour nos tables), si ce n'est pas le cas, il est possible de passer de Wayland à Xorg au démarrage :
    - Aller dans les paramètres, section utilisateur et vérifier que `Connexion automatique` est désactivé
    - Maintenant, déconnectez-vous
    - Sur la page de connexion, vous trouverez en bas à droite un bouton de paramètre vous permettant de changer le système de fenêtrage utilisé

3) Pour calibrer l'écran, taper simplement `xinput_calibrator` dans un terminal et suiver les instructions à l'écran :

![](https://cdn.discordapp.com/attachments/992077049344819281/1079716101543428156/raspberry-pi-xinput_calibrator.png)

## Sauvegarder les réglages

4) Une fois la calibration finie, vérifier le bon fonctionnement. Vous trouverez dans la console du texte à sauvegarder dans un fichier `sudo gedit /usr/share/X11/xorg.conf.d/99-calibration.conf`pour mémoriser les réglages effectués et les charger à chaque démarrage.

![](https://cdn.discordapp.com/attachments/992077049344819281/1079718153153683456/xinput_calibrator-console-screen.png)
