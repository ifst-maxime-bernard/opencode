# MCP Tools Usage

## Principe général
- Si un outil MCP peut fournir une réponse plus précise que la connaissance interne du modèle, **l'utiliser en priorité**.
- Ne jamais supposer des informations (signatures de fonctions, détails de tickets, erreurs) sans interroger l'outil approprié d'abord.

---

## Context7 — Documentation externe

- **TOUJOURS** utiliser Context7 pour rechercher la documentation de toute bibliothèque ou framework externe.
- Ne jamais supposer la signature d'une fonction, le nom d'un paramètre ou le comportement d'une méthode sans avoir interrogé Context7 au préalable.
- Séquence obligatoire :
  1. `resolve-library-id` → obtenir l'ID Context7 exact de la bibliothèque.
  2. `query-docs` → interroger la documentation avec cet ID.
- Ne jamais appeler `query-docs` directement sans passer par `resolve-library-id` d'abord.

---

## Sentry — Monitoring et erreurs

- Utiliser les outils Sentry dès qu'un ID d'issue, un ID d'événement ou une URL Sentry est fourni.
- Prioriser `get_issue_details` pour analyser un crash ou une exception en profondeur.
- Outils disponibles selon le contexte :
  - `get_issue_details` → analyse complète d'un crash avec stacktrace.
  - `search_issues` → lister des issues groupées (ne pas utiliser pour compter).
  - `search_events` → compter des erreurs, agrégations, statistiques.
  - `get_issue_tag_values` → distribution par browser, URL, environment, etc.

---

## Zoho Projects — Gestion de projet

- Utiliser les outils Zoho Projects pour récupérer le détail d'une tâche ou d'un ticket si un ID ou un nom est mentionné.
- Séquence typique :
  1. `getAllPortals` → récupérer le portal ID si inconnu.
  2. `getAllProjects` → récupérer le project ID si inconnu.
  3. `getTaskDetails` ou `getIssueDetails` → obtenir les détails de la tâche/issue.
