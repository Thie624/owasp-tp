# SQL Injection 2 – Tests sur paramètres GET (time-based)

## Description
Des tests d’injection SQL ont été réalisés sur les paramètres GET de l’application,
notamment le paramètre `page`, afin d’identifier une éventuelle injection SQL
de type logique ou time-based.

## Étapes pour reproduire
1. Accéder à l’application via le navigateur.
2. Modifier le paramètre `page` dans l’URL.
3. Injecter des payloads SQL de type logique et time-based.
4. Observer le comportement de l’application.

Payloads testés :
- `'`
- `ORDER BY 1`, `ORDER BY 2`, etc.
- `AND SLEEP(5)`
- `AND IF(1=1,SLEEP(5),0)`
- `AND IF(1=2,SLEEP(5),0)`

## Résultat
Aucune différence de comportement ni délai mesurable n’a été observé entre les
différents tests. Aucun message d’erreur SQL n’est affiché.

## Conclusion
Aucune injection SQL exploitable n’a été identifiée sur les paramètres GET testés.
L’application semble protégée contre ce type d’attaque.

## Remédiation
- Utiliser exclusivement des requêtes préparées.
- Valider les paramètres côté serveur.
- Désactiver l’affichage des erreurs SQL en production.
