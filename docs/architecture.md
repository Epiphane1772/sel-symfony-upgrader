# Architecture

SEL Symfony Upgrader is implemented as a single Bash command.

## Main components

### Environment validation

The command verifies:

- Bash execution
- Git availability
- PHP version
- Composer availability
- GitHub CLI authentication
- GitHub SSH authentication

### Repository preparation

The command either clones the selected repository or updates an existing local checkout.

It verifies that the local directory belongs to the requested GitHub repository and refuses to continue when uncommitted changes exist.

### Symfony detection

The command requires:

- composer.json
- composer.lock
- symfony/framework-bundle

### Dependency upgrade

The command updates Symfony package constraints to 7.4 and configures Symfony Flex to restrict Symfony packages to the 7.4 release line.

Composer performs the dependency resolution with related dependencies enabled.

### Validation

The command performs:

- Composer file validation
- Composer security auditing
- reinstall from composer.lock
- Symfony application information check
- YAML linting
- service-container linting
- Twig linting
- PHPUnit execution when tests exist

### Git workflow

The command creates a dated security branch, commits changes, pushes the branch and creates a pull request.

### Safety boundary

The command stops at pull-request creation.

Merging, deployment and database migration remain deliberate manual operations.
