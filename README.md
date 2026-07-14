# SEL Symfony Upgrader

A command-line utility that automates safe Symfony application upgrades to Symfony 7.4 LTS.

It creates a dedicated Git branch, upgrades Composer dependencies, validates the application, performs a security audit, pushes the result and opens a GitHub pull request.

It never merges the pull request and never deploys the application automatically.

## Features

- Clones or updates a GitHub repository
- Verifies that the repository is a Symfony Framework application
- Requires PHP 8.2 or newer
- Creates a dated security branch
- Updates Symfony packages consistently to Symfony 7.4 LTS
- Updates related Composer dependencies
- Validates composer.json and composer.lock
- Runs Composer security auditing
- Reports abandoned Composer packages separately
- Reinstalls dependencies from the generated lock file
- Validates Symfony YAML configuration
- Validates the dependency-injection container
- Validates Twig templates
- Runs PHPUnit when tests are present
- Commits and pushes the upgrade
- Creates a GitHub pull request
- Does not merge or deploy automatically

## Requirements

The following commands must be installed:

- Bash
- Git
- GitHub CLI
- PHP 8.2 or newer
- Composer
- SSH

GitHub CLI must be authenticated:

    gh auth login

GitHub SSH authentication must also work:

    ssh -T git@github.com

## Installation

Clone the repository:

    git clone git@github.com:Epiphane1772/sel-symfony-upgrader.git "$HOME/Projects/sel-symfony-upgrader"

Create a command directory:

    mkdir -p "$HOME/bin"

Create the command link:

    ln -sfn "$HOME/Projects/sel-symfony-upgrader/bin/upgrade-symfony-74" "$HOME/bin/upgrade-symfony-74"

Add the command directory to your PATH:

    printf '\n%s\n' 'export PATH="$HOME/bin:$PATH"' >> "$HOME/.zprofile"

Open a new Terminal window.

## Usage

    upgrade-symfony-74 OWNER/REPOSITORY

Example:

    upgrade-symfony-74 Epiphane1772/api-idf.transports.express-v1.2

## What happens

The utility:

1. Verifies required programs and authentication.
2. Clones or updates the selected repository.
3. Detects the repository default branch.
4. Verifies composer.json, composer.lock and Symfony FrameworkBundle.
5. Creates a branch named with the current date.
6. Changes Symfony constraints to Symfony 7.4.
7. Runs a full Composer dependency update.
8. Runs Composer validation and security auditing.
9. Reinstalls dependencies from composer.lock.
10. Runs Symfony configuration checks.
11. Runs PHPUnit when test files exist.
12. Commits and pushes the changes.
13. Creates a GitHub pull request.

## Safety

The utility intentionally does not:

- merge pull requests
- deploy applications
- modify production servers
- run database migrations
- delete databases
- change environment secrets
- commit .env.local
- ignore Composer security advisories

Review every generated pull request before merging.

## Branch naming

Branches use this format:

    security/symfony-7.4-YYYY-MM-DD

## Commit message

The generated commit uses:

    security: upgrade Symfony dependencies to 7.4

## Limitations

- The current release specifically targets Symfony 7.4 LTS.
- Applications requiring custom upgrade code may still need manual changes.
- A successful configuration lint does not replace application-specific tests.
- PHPUnit is skipped when no test files are present.
- Abandoned packages are reported but do not necessarily represent vulnerabilities.
- Database migrations are never executed automatically.

## Documentation

- Architecture: docs/architecture.md
- Usage examples: docs/examples.md
- Troubleshooting: docs/troubleshooting.md
- Release history: CHANGELOG.md
- Security policy: SECURITY.md
- Contribution guide: CONTRIBUTING.md

## License

This project is available under the MIT License.
