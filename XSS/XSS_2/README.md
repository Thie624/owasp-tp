# XSS 2 – XSS réfléchi via paramètre GET

## Description
Une vulnérabilité de type XSS réfléchi a été identifiée via le paramètre GET `page`.
Le contenu fourni par l’utilisateur est interprété par le navigateur sans filtrage
permettant l’exécution de code JavaScript.

## Étapes pour reproduire
1. Accéder à l’application via le navigateur.
2. Modifier le paramètre `page` dans l’URL.
3. Injecter un script JavaScript encodé.
4. Valider la requête.

## Preuve
L’injection du payload JavaScript provoque l’exécution d’un script côté client,
confirmée par l’apparition d’une fenêtre JavaScript.

URL de test :
http://192.168.10.12/?page=%3Cscript%3Ealert(1)%3C/script%3E


## Remédiation
- Filtrer et valider strictement les paramètres GET.
- Échapper les caractères spéciaux avant affichage.
- Mettre en place une Content Security Policy (CSP).
### Capture – Exécution du script JavaScript
![xss-2](https://github.com/user-attachments/assets/85027c80-bfaf-4ba4-82b5-49b9ea7f21f3)

![xss-2 2](https://github.com/user-attachments/assets/4dde8d09-788d-4b66-a4f3-0b7fa86f5c48)

