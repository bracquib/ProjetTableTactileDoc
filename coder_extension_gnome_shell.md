# Documentation création d'une extension Gnome Shell 

## Premièrement, qu'est ce que GNOME ?

GNOME (GNU Network Object Model Environment) est un **environnement de bureau** pour plateformes GNU/Linux et les systèmes UNIX, il permet d'utiliser les différentes fonctionnalités d'un pc **via une interface graphique** (terminal, editeur de texte, gestionnaire de fichiers, de tâches...)

GNOME est l'environnement par défaut installé sur les versions récentes d'Ubuntu, qui est la distribution choisie pour nos tables tactiles.

![](https://cdn.discordapp.com/attachments/992077049344819281/1072181909402173600/gnome-42-new-shell-theme-screenshot.png)

## Parfait, mais du coup qu'est ce que GNOME Shell ?

C'est **le coeur de l'interface graphique** de l'environnement de GNOME. GNOME Shell définit entre autres le tableau de bord, la zone de notification et le sélecteur de fenêtres de GNOME.

![](https://cdn.discordapp.com/attachments/992077049344819281/1072182399179436062/GNOME-42-Desktop.png)


GNOME Shell utilise le système de fenêtrage **Wayland ou Xorg** pour fonctionner. Pour notre extension et pour nos tables tactiles, nous avons besoin d'utiliser Xorg (on en a besoin pour le retournement d'écran proposé par `xrandr` et pour installer certains plugins pour mieux gérer le multitouches).

GNOME Shell intégre également **un système d'extensions** (écrites en JavaScript) qui permettent de personnaliser le GNOME Shell et d'ajouter/modifier des fonctionnalités. Il y a également un service Web ( https://extensions.gnome.org/ ) où tout développeur peut proposer et partager ses extensions. 

On va donc se servir de ce système pour développer un bouton accessible dans la barre supérieure (accessible à tout moment), et qui permettra à l'utilisateur de la tablette tactile de retourner le contenu affiché pour qu'il soit toujours bien orienté.

## Rentrons dans le vif, comment coder une extension GNOME Shell ?

Inspiré par : https://gjs.guide/extensions/overview/anatomy.html#extension-meta-object

Toute extension Gnome Shell est composée de 2 fichiers à placer dans `~/.local/share/gnome-shell/extensions/[NomDossierDeLextension]/` :
- **metadata.json** : certains champs sont obligatoires dont : 
    ```json {
    "uuid": "example@vincent",
    "name": "Example",
    "description": "Description de l'extension.",
    "shell-version": [ "3.38", "40" ],
    "url": "https://gricad-gitlab.univ-grenoble-alpes.fr/Projets-INFO4/22-23/14/projet",
    "version": 1
    ```
    - *uuid* : champ d'identification unique de l'extension, décomposé en 2 parties par @. Il est conseillé d'avoir un petit texte décrivant le but de l'extension à gauche et un domaine a votre nom (si disponible a droite). Ce nom doit être identique à celui du nom du dossier dans lequel les fichiers de l'extension se trouve.
    - *name* : nom court descriptif de l'extension.
    - *description* : description un peu plus longue de l'extension, on peut utiliser les \n et les \t.
    - *shell-version* : liste de chaînes de caractères pour décrire les versions gnome supportées par l'extension. Pour les versions jusqu'à GNOME 3.38, il faut les 2 composants de la version, à partir de GNOME 40 ce n'est plus nécessaire.
    - *url* : une adrese vers un repo git où le code source est disponible et les problèmes peuvent être remontés. Pas obligatoire si le but n'est pas de proposé l'extension sur le service web.
- **extension.js** : coeur de l'extension. Il contient trois point de branchement (function hook) `init()` , `enable()` , `disable()` utilisé par GNOME Shell pour charger et (dés)activer l'application. Le reste est libre, on peut notamment par exemple appeler les librairies Streamlit (ST) pour programmer un bouton et ui.main pour le placer dans l'interface de GNOME Shell.

On peut également ajouter un **fichier css** pour modifier le visuel des widgets de l'extension ou de tout GNOME Shell.

Enfin, on peut aussi définir un fichier **prefs.js** pour modifier les paramètres de l'extension depuis la page suivante : https://extensions.gnome.org/local/ (après avoir installé une extension dans le navigateur et un connecteur vers l'hôte (API pour accéder à des applications locales depuis le browser))

Une fois les 2 fichiers programmés, rafraichissez gnome-shell en appuyant sur **Alt+F2**, puis rentrer 'r' dans le champ proposé et appuyer sur Entrée pour valider.

Ensuite activez l'extension en éxecutant la commande suivante : 
`gnome-extensions enable [NomDsMetadata]`

Enfin rafraichissez gnome-shell comme vu précédemment, votre extension est maintenant utilisable.

## Programmation d'un bouton pour tourner l'écran de 90 dégrés

On a suivi les étapes précédentes, mais la fonction appelée par le bouton (programmé en js via la librairie **St**) est la suivante : 
```
function _rotateButton () {
Util.spawnCommandLine("bash /home/vincentdcr/rotateScript.sh")
}
```
On exécute donc un script bash qui va se servir de **xrandr** (un outil en ligne de commande qui utilise une extension du système de fenêtrage Xorg pour modifier les paramètres d'affichage d'un écran). Notamment, utiliser la commande suivante tournera l'écran vers la gauche : `xrandr -o left`
