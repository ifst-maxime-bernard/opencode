# Shared Guidelines — PHP / Symfony / DDEV

Common baseline applied by all agents in this project.

---

## PHP standards
- **Version**: PHP 8.2+
- **Strict typing**: `declare(strict_types=1);` at the top of every file
- **Style**: PSR-12
- **Type hints**: mandatory everywhere — parameters, return types, properties
- **Modern features to prefer**: readonly properties, enums, named arguments, match expressions, first-class callable syntax
- **Error handling**: explicit — never swallow exceptions silently

## Symfony conventions
- **Configuration format**: PHP attributes (not YAML/XML) for routing, Doctrine mappings, validation, serialization
- **Dependency injection**: constructor injection only; no setter injection
- **Controllers**: thin — delegate to services; use DTOs, never raw entities, for input/output
- **Services**: single responsibility; one class = one job
- **Forms**: Symfony Form component for all user input handling and validation
- **Async**: Symfony Messenger for background/async operations
- **Cache**: apply Symfony cache attributes/strategies where reads are expensive
- **Migrations**: always generate with `ddev console doctrine:migrations:diff` after schema changes; never hand-edit migration files unless necessary

## DDEV workflow
| Action | Command |
|---|---|
| Symfony console | `ddev console <cmd>` |
| Composer install/require | `ddev composer <cmd>` |
| PHP lint a file | `ddev php -l <file>` |
| Arbitrary shell in container | `ddev exec <cmd>` |

**Rule**: all commands that touch the application runtime (PHP, Composer, DB) must run inside the DDEV container via the above shortcuts — never against the host PHP/Composer directly.

## Code quality checklist (apply before finishing any task)
- [ ] `ddev php -l` passes on every modified file
- [ ] No unused `use` imports
- [ ] No hardcoded credentials, DSNs, or API keys
- [ ] No `var_dump`, `dd()`, or debug output left in code
- [ ] PHPDoc added only when types alone don't convey intent
- [ ] New/changed DB schema → migration generated and reviewed
- [ ] Run test suite
