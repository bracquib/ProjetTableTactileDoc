# Documentation réinstallation linux 

## Raison initiale 
lors de l'inventaire et de la prise en main des tables tactiles : 
- problème de version et de connection a internet ( un module wifi manquant pour une des tables, des ubuntu à mettre à jour )
- un mot de passe user inconnu, donc impossible de mettre a jour les tables ni d'installer notre serveur local
- les écrans tactiles ne sont pas gérés par ubuntu installé dessus, donc on peut juste faire des clics simples et on ne peut pas faire : 
    - de clics droits
    - de drags
    - de multi-touch 

- une des deux tables utilisées a besoin de changement de pile cm, cmos batterie a plat https://www.amazon.com/Eunicell-CR2032-Lithium-Blister-Batteries/dp/B00PNW4HSG

## Démarche de réinstallation 
 
puisqu'il existe des versions tactiles de linux ( ubuntu touch) conçues pour des tablette, ou même des packages qui permettent de passer en mode multi touch, on va essayer de régler ce problème, et on en profite pour mettre la dernière version d'ubuntu dans un soucis de long terme.

Il y a deux cas de tests, un avec une installation d'ubuntu touch, une version d'ubuntu créé pour les tablettes et smartphones, comme ubuntu sur pc, elle est gratuite et open source.
:::danger
Au final, après plusieurs tests, ubuntu touch ne fonctionne pas, l'installation matérielle est reconnue comme un écran tactile et un ordinateur, pas un ensemble des deux, donc l'installation d'ubuntu touch a échouée.
:::


La deuxième option est d'installer ubuntu pc "basique" et de paramétrer celui ci pour gérer les utilisations tactiles avec des paquets déja existants (touche gg, unclutter, etc...)

## Inventaire existant 
On commence par faire un inventaire des fichiers présents rajoutés sur la table tactile, pour voir s'il y a des ressources utiles au projet table tactile 

( au final il y a uniquement les fichiers du jeu de l'année d'avant, et quelques jeux installés via l'app store rien d'autre)

Table 1 ( ubuntu 22.04 ) i5 4250u / 4Go de ram : 
- Démontage du boitier, pour régler le problème de la pile + installation ubuntu touch
- Pas de wifi

2ème Table Digitale (ubuntu 22.04 ) : i5 4250u / 4Go de ram 
- wifi
- pile ok

3ème Table basse Tactile ( Fablab) : i5 4250 / 6Go de ram
- wifi
- pile ok

# Documentation de l'installation linux 
Prérequis :

- Un ordinateur sur lequel vous souhaitez installer Ubuntu 22.04
- Une clé USB d'au moins 4 Go
- Le fichier ISO d'installation d'Ubuntu 22.04, que vous pouvez télécharger à partir du site web d'Ubuntu : https://ubuntu.com/download
## Étape 1 : Création d'une clé USB de démarrage

- Insérez la clé USB dans l'ordinateur.
- Téléchargez et installez le programme de création de clé USB de démarrage, comme Etcher ou Rufus.
- Lancez le programme de création de clé USB de démarrage et sélectionnez le fichier ISO d'installation d'Ubuntu 22.04 que vous avez téléchargé.
- Sélectionnez la clé USB comme périphérique de destination et lancez la création de la clé USB de démarrage.
## Étape 2 : Configuration du BIOS de l'ordinateur

- Redémarrez l'ordinateur et appuyez sur la touche appropriée pour accéder au BIOS pendant le démarrage (généralement la touche Suppr, F2 ou F10).
- Dans le BIOS, recherchez l'option "Boot Order" ou "Boot Priority".
- Modifiez l'ordre de démarrage pour que la clé USB soit en première position de la liste.
- Sauvegardez les modifications et quittez le BIOS.
## Étape 3 : Installation d'Ubuntu 22.04

- Redémarrez l'ordinateur et attendez que le programme d'installation d'Ubuntu se charge depuis la clé USB.
- Sélectionnez votre langue et cliquez sur le bouton "Installer Ubuntu".
- Sélectionnez les options d'installation souhaitées (comme le partitionnement du disque dur) et suivez les instructions à l'écran pour terminer l'installation.
- Une fois l'installation terminée, retirez la clé USB et redémarrez l'ordinateur.

Voilà, vous avez maintenant installé Ubuntu 22.04 sur votre ordinateur à l'aide d'une clé USB de démarrage.

# Documentation de la tacticité.
Prérequis :

- Trois machines NUC
- Écran tactile Egalax
- Ubuntu 22.04 ouvert en mode Xorg
- Connexion Internet

## Étape 0 : Installation de lightdm 
lightdm est une installation nécéssaire pour un bon fonctionnement des drivers eGalax (demandé par l'installer du driver) 


## Étape 1: Installation des pilotes Linux de l'écran tactile Egalax

1. Connectez l'écran tactile Egalax à la machine NUC.
Ouvrez un terminal et tapez la commande suivante pour installer les pilotes Linux de l'écran tactile Egalax :
 ```bash=
sudo apt-get install xserver-xorg-input-evtouch
```
2. Redémarrez la machine pour appliquer les changements.
## Étape 2: Installation du driver Egalax

1. Téléchargez le driver Egalax sur le site web du fabricant : 
- https://www.eeti.com/drivers_Linux.html

2. Extrayez le fichier téléchargé et ouvrez un terminal dans le dossier extrait.
3. Tapez la commande suivante pour installer le driver :

```bash=
tar -xzf eGTouch_v2.5.9321.L-x.tar.gz
cd eGTouch_v2.5.9321.L-x
sh setup.sh
```
ps: on a pris une version au dessus ici.

4. Redémarrez la machine pour appliquer les changements.
## Étape 3: Installation de TouchGG

Ouvrez un terminal et tapez la commande suivante pour ajouter le PPA de TouchGG :

```bash =
sudo add-apt-repository ppa:touchgfx-team/touchgg
```
Ensuite, tapez la commande suivante pour mettre à jour la liste des paquets :
```bash=
sudo apt-get update
```
Enfin, tapez la commande suivante pour installer TouchGG :
```bash=
sudo apt-get install touchgg
```
## Étape 4: Installation de Touché

Ouvrez un terminal et tapez la commande suivante pour télécharger le fichier d'installation de Touché :

```bash=
wget https://github.com/JoseExposito/touche/releases/download/v2.0.2/touche_2.0.2_amd64.deb

```
Ensuite, tapez la commande suivante pour installer Touché :
```bash=
sudo dpkg -i touche_2.0.2_amd64.deb
```

## Étape 6: Configuration de TouchGG et Touché

- Lancez TouchGG en tapant la commande suivante dans un terminal :
```bash=
touchgg
```

Cliquez sur l'icône d'engrenage en haut à droite de la fenêtre pour accéder aux paramètres.
Dans la section "Input Device", sélectionnez la référence de l'écran Egalax affichée pour l'écran tactile Egalax.
Dans la section "Actions", ajoutez les gestes multitouch que vous souhaitez utiliser. ( ici, on paramètre sur Firefox)

- Enregistrez les modifications et fermez la fenêtre.
Lancez Touché en tapant la commande suivante dans un terminal :
Dans la section "Gesture Engine", sélectionnez "TouchGG".
Enregistrez les modifications et fermez la fenêtre.
(vous pouvez également passer par l'icone du bureau)

## Étape 5: Test du multitouch

Lancez une application qui prend en charge le multitouch, comme un navigateur web.
Effectuez les gestes multitouch que vous avez configurés dans TouchGG pour vérifier que le multitouch fonctionne correctement.
Voilà, vous devriez maintenant avoir réussi à activer le multitouch sur votre écran tactile Egalax sous Ubuntu 22.04 en utilisant TouchGG et Touché
(dans notre cas, fonctionne puisque certaines commandes marchent, mais le type d'installation de base faite par l'entreprise avant nous, ne semble permettre d'identifier le **premier clic** comme un clic de souris, comme un pavé tactile d'ordinateur)
