# Symfony Stack

## Language & Framework
- Language: **PHP 8.2+**
- Framework: **Symfony 7.x**
- Package manager: **Composer**
- Local dev environment: **DDEV**

## PHP Conventions
- `declare(strict_types=1);` is mandatory in every PHP file.
- Use full type hints on all properties, parameters, and return types.
- Use PHP 8.2+ features: readonly properties, enums, named arguments, fibers.
- Use PHP attributes for routing, validation, Doctrine mappings, and event listeners. Never use YAML or XML for these.

## Symfony Conventions
- Controllers must be thin: delegate business logic to services.
- Never pass raw Doctrine entities to controllers or templates — use DTOs.
- Use Symfony Messenger for async processing.
- Use Symfony Validator with attribute-based constraints.
- Use API Platform for REST/GraphQL endpoints where applicable.
- Use Symfony Security with voters for access control.

## Doctrine Conventions
- Use attribute-based Doctrine mappings.
- Generate migrations with `ddev console doctrine:migrations:diff` — never edit the schema manually.
- Always review generated migrations before applying.
- Avoid N+1 queries: use JOIN FETCH or batch loading.

## Code Style
- Follow PSR-12.
- Use PHP-CS-Fixer with the project's `.php-cs-fixer.dist.php` config.
- Class names: PascalCase. Methods/variables: camelCase. Constants: SCREAMING_SNAKE_CASE.
