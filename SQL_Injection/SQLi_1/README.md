# SQL Injection 1 – Tests sur paramètres POST

## Description
Des tests d’injection SQL ont été réalisés sur les paramètres envoyés via le formulaire
de la page `survey`, notamment le champ `valeur` (Grade) et le champ caché `sujet`.

## Étapes pour reproduire
1. Accéder à la page `survey`.
2. Ouvrir l’inspecteur du navigateur.
3. Modifier les valeurs envoyées par le formulaire (payloads SQL).
4. Soumettre le formulaire.

Payloads testés :
- `'`
- `1 OR 1=1`
- `1/0`
- `2'` (champ caché `sujet`)

## Résultat
Aucune erreur SQL ni modification du comportement de l’application n’a été observée.
Les paramètres semblent correctement filtrés ou castés côté serveur.

## Remédiation
- Utiliser des requêtes préparées (prepared statements).
- Valider et typer strictement les entrées utilisateur.
- Ne jamais faire confiance aux données côté client.
### Capture – Tests SQLi sur paramètres POST (aucun impact)
![Test page=members](https://github.com/user-attachments/assets/2f88b8d6-2928-484e-8000-5638357cd324)


