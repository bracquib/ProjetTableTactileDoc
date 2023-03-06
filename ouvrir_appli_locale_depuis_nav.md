## Mettre en place l'URI unique :

Pour pouvoir ouvrir une page dans un navigateur, il faut un lien vers celle-ci, il en va de même pour une application locale. C'est alors à nous de générer un lien utilisable par le navigateur. Pour cela, sous Ubuntu, on va modifier le fichier .desktop (qui gère le raccourci pour afficher et ouvrir l'application depuis le menu d'applications d'Ubuntu).

Dans ce dernier on va rajouter une ligne : `MimeType=x-scheme-handler/<custom-protocol>` trouvable dans `/usr/share/applications/` (il faut ouvrir le fichier avec sudo pour le modifier). On modifie donc et on définit un handler web (x-scheme-handler, un type MIME) pour ouvrir l'application depuis un URI.

Ensuite on utilise xdg-mime pour mettre à jour l'environnement de bureau (Gnome ici) pour faire de l'application (premier argument), l'application par défaut pour ouvrir les fichiers de type (2ème argument) :`xdg-mime default <nom-application-modifiée>.desktop x-scheme-handler/<custom-protocol>`

Enfin, lancer la commande : `sudo update-desktop-database /usr/share/applications`. Cette commande à pour but de construire une base de données en cache des types MIME supportés par les applications (fichiers .desktop) ainsi qu'une liste des applications qui gère un certain type MIME.

Pour tester que l'URI unique a bien été créé correctement, taper dans la barre d'URL de votre navigateur : **[custom-protocol]:**  puis Entrée. Votre application s'est normalement lancée par-dessus votre navigateur. (Possiblement après un pop-up vous demandant de confirmer l'ouverture)
    
