# DDEV Tooling

## Principle
All commands that invoke PHP, Composer, or Symfony console **must** go through DDEV.
Never run `php`, `composer`, or `bin/console` directly on the host.

## Command Reference
| Action | Command |
|---|---|
| PHP CLI | `ddev php <args>` |
| Composer | `ddev composer <args>` |
| Symfony console | `ddev console <args>` |
| PHPUnit | `ddev php vendor/bin/phpunit` |
| PHPStan | `ddev php vendor/bin/phpstan analyse` |
| PHP-CS-Fixer (check) | `ddev php vendor/bin/php-cs-fixer fix --dry-run --diff` |
| PHP-CS-Fixer (fix) | `ddev php vendor/bin/php-cs-fixer fix` |
| Rector (dry-run) | `ddev php vendor/bin/rector process --dry-run` |
| Rector (apply) | `ddev php vendor/bin/rector process` |
| Doctrine migration diff | `ddev console doctrine:migrations:diff` |
| Doctrine migration run | `ddev console doctrine:migrations:migrate` |
| Cache clear | `ddev console cache:clear` |
| Start environment | `ddev start` |
| Stop environment | `ddev stop` |

## Linting
- Lint a single PHP file: `ddev php -l <path/to/file.php>`
- Run PHP-CS-Fixer on a single file: `ddev php vendor/bin/php-cs-fixer fix <file> --dry-run --diff`

## DDEV Add-ons
- Prefer `ddev get <addon>` over manual Docker Compose overrides.
- Never hardcode secrets in `.ddev/` config — use `.ddev/.env.local` (gitignored).
