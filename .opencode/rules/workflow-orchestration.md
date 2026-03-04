# Workflow Orchestration

## Décomposition des tâches
- Toujours **décomposer les tâches complexes** en sous-tâches atomiques et indépendantes avant de commencer.
- Identifier explicitement les dépendances entre sous-tâches pour déterminer l'ordre d'exécution.

## Parallélisme
- **Maximiser le parallélisme** : lancer plusieurs appels d'outils simultanément dès qu'ils sont indépendants.
- Exemples de parallélisation systématique :
  - Lecture de plusieurs fichiers en une seule passe.
  - Lancement de plusieurs sous-agents (Task) pour des analyses ou modifications non liées.
  - `git status`, `git diff` et `git log` toujours appelés en parallèle.

## Analyse avant modification
- **Toujours analyser l'existant** avant de proposer ou d'appliquer une modification :
  - Lire les fichiers concernés.
  - Identifier les patterns et conventions déjà en place.
  - Vérifier l'impact sur les fichiers dépendants.
- Ne jamais supposer la structure d'un fichier sans l'avoir lu.
