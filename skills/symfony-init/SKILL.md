---
name: symfony-init
description: Initialise un projet Symfony 7 moderne avec DDEV, Bitbucket CI/CD, PHPStan, PHP-CS-Fixer et Rector.
license: MIT
metadata:
  version: "1.0"
  framework: Symfony 7
  php_version: "8.3"
---

# symfony-init

Initialise un projet Symfony 7 avec DDEV, Bitbucket CI et QA tools.

## Instructions pour l'agent

Ce skill permet d'automatiser l'initialisation d'un nouveau projet Symfony 7 en suivant les standards de qualité (PHPStan, PHP-CS-Fixer, Rector) et en configurant l'environnement de développement local (DDEV) ainsi que l'intégration continue (Bitbucket Pipelines).

### Étapes d'initialisation

1.  **Configuration DDEV** :
    *   Exécuter `ddev config --project-type=php --php-version=8.3 --docroot=public`.
    *   Lancer l'environnement : `ddev start`.

2.  **Installation Symfony** :
    *   Utiliser la commande : `ddev composer create "symfony/skeleton"`.
    *   Installer les composants essentiels : `ddev composer require webapp`.

3.  **Mise en place des outils de QA** :
    *   Copier les fichiers de configuration depuis le dossier `references` du skill vers la racine du projet :
        *   `references/phpstan.neon` -> `phpstan.neon`
        *   `references/php-cs-fixer.dist.php` -> `.php-cs-fixer.dist.php`
        *   `references/rector.php` -> `rector.php`
    *   Installer les dépendances de dev :
        ```bash
        ddev composer require --dev phpstan/phpstan phpstan/phpstan-symfony phpstan/phpstan-doctrine friendsofphp/php-cs-fixer rector/rector
        ```

4.  **Configuration CI/CD** :
    *   Copier `references/bitbucket-pipelines.yml` -> `bitbucket-pipelines.yml` à la racine.
    *   Ajuster les variables d'environnement dans Bitbucket (DATABASE_URL, etc.).

5.  **Configuration de l'observabilité (Monolog)** :
    *   Copier le template de référence dans le projet :
        ```bash
        cp references/monolog.yaml config/packages/monolog.yaml
        ```
    *   Vérifier que le répertoire `var/log/` est bien ignoré par Git
        (`.gitignore` Symfony l'exclut par défaut) et que la rotation de
        30 jours convient à la politique de rétention du projet.
    *   En production, privilégier le format JSON (`monolog.formatter.json`)
        pour une ingestion facilitée par Loki, Datadog ou ELK.

6.  **Finalisation** :
    *   Initialiser le dépôt Git.
    *   Créer un premier commit avec la structure de base.

### Utilisation des templates
Pour copier un template, utilise la commande `cp` (ou l'outil `write` avec le contenu du template) vers la destination finale dans le projet de l'utilisateur.
