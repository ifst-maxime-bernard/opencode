---
description: Met à jour Symfony vers la version majeure cible ($1) en suivant un workflow itératif et sécurisé.
---

# Symfony Major Upgrade ($1)

Cette commande orchestre la montée de version majeure de Symfony vers la version cible **$1**.

## 🚀 Workflow d'Orchestration (Agent Manager)

L'agent Manager doit piloter la mise à jour en suivant scrupuleusement ces étapes itératives jusqu'à atteindre la version **$1**.

### 1. Analyse Initiale
- Détecter la version actuelle de Symfony via `composer.json` (`extra.symfony.require`) ou `ddev composer show symfony/framework-bundle`.
- Déterminer les étapes intermédiaires nécessaires (ex: 5.3 -> 5.4 -> 6.4 -> 7.0).

### 2. Cycle de Mise à Jour (Boucle par version majeure)

Pour chaque saut de version majeure vers la cible $1 :

#### A. Alignement sur la dernière mineure (ex: x.4)
- Si la version actuelle n'est pas la dernière mineure de sa branche (ex: 5.3 au lieu de 5.4) :
  - Mettre à jour `composer.json` vers la version x.4.
  - Exécuter `ddev composer update`.
  - Corriger toutes les dépréciations signalées (refactor) avant de tenter le saut majeur.

#### B. Correction des Dépréciations
- Configurer et vérifier `rector.php` pour cibler la bonne version de PHP et de Symfony ($1).
- Utiliser un agent `refactor` pour automatiser les renommages de classes et de méthodes dépréciées via Rector :
  - Exécuter `ddev php vendor/bin/rector process` avec les jeux de règles (sets) appropriés pour la version cible.
- Analyser les logs de tests et de console pour identifier les "Deprecations" restantes et effectuer les corrections manuelles.
- Valider les modifications de Rector par une analyse statique (`ddev php vendor/bin/phpstan`) et le passage des tests.
- Ne jamais tenter un saut majeur s'il reste des dépréciations actives dans le code.

#### C. Saut vers la Majeure Suivante
- Modifier `composer.json` :
  - Mettre à jour `extra.symfony.require` vers la version majeure suivante.
  - Ajuster les contraintes des packages `symfony/*` si nécessaire.
- Exécuter `ddev composer update`.
- Mettre à jour les recettes Symfony Flex : `ddev composer recipes:update`.

#### D. Validation et Tests
- Lancer la suite de tests complète : `ddev composer test` ou `ddev php vendor/bin/phpunit`.
- Vérifier l'analyse statique : `ddev php vendor/bin/phpstan`.
- L'étape n'est validée que si les tests sont au vert et sans erreurs fatales.

### 3. Finalisation
- Répéter le cycle jusqu'à ce que la version de Symfony corresponde à **$1**.
- Effectuer un nettoyage final (`ddev console cache:clear`).

## ⚠️ Consignes de Sécurité
- Effectuer un commit après chaque étape réussie (mineure stable, corrections dépréciations, saut majeur).
- En cas d'échec de `composer update`, analyser les conflits de dépendances et suggérer les mises à jour de bundles tiers nécessaires.
- Utiliser systématiquement les commandes `ddev` pour toutes les opérations CLI.
