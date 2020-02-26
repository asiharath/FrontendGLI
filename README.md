# gliproject

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run start or npm start
```

## Guide
### Introduction
Nous site vous permet de calculer automatiquement quel sera le trajet le plus court de chez vous à votre travail.

### Connexion
Nous utilisons ici les cookies pour garder les authentifications en mémoire donc vous n'allez pas pouvoir naviguer sans vous être connectez.

Vous pouvez à la page de connexion aller vers la page d'enregistrement malheuresement vous n'allez pas pouvoir vous enregistrer (problème de CORS avec le back pour le POST).

Vous allez devor utiliser un compte déjà crée ou vous en créerun en fesant un requête via Postman/Insomnia ou tout genre d'outil qui n'utilise pas de domaine différent.

### Site
Sur la page du site le logo vous permettra de toujours revenir à l'acceuil, vous allez avoir la possiblité de modifier votre profile mais comme dit précédemment il y a un problème de CORS pour les requêtes HTTP POST, DELETE et PUT sauf pour GET.
Nous avons utilisé l'API google map pour calculer le trajet plus entre chez vous et votre travail.
