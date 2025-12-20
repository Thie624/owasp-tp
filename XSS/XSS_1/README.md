# XSS 1 – Injection HTML stockée (Grade)

## Description
Une vulnérabilité de type XSS (injection HTML stockée) a été identifiée sur la page `survey`.
Le champ de sélection de la note (Grade) n’effectue pas de validation côté serveur et accepte
des valeurs arbitraires injectées via la modification du DOM.

## Étapes pour reproduire
1. Accéder à la page `survey`.
2. Ouvrir l’inspecteur du navigateur.
3. Modifier une option du champ `select` (Grade).
4. Remplacer la valeur numérique par une valeur arbitraire (ex: `XSS`).
5. Sélectionner cette valeur dans le menu déroulant.

## Preuve
La valeur injectée est enregistrée et réaffichée dans l’interface utilisateur à la place
d’une valeur numérique attendue.

## Remédiation
- Valider strictement les entrées côté serveur (valeurs numériques uniquement).
- Implémenter une liste blanche des valeurs autorisées (1 à 10).
- Échapper les données avant affichage côté client.
