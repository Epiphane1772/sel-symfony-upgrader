# Contributing

Contributions are welcome.

## Development setup

Clone the project:

    git clone git@github.com:Epiphane1772/sel-symfony-upgrader.git
    cd sel-symfony-upgrader

Validate Bash syntax:

    bash -n bin/upgrade-symfony-74

Run ShellCheck when installed:

    shellcheck bin/upgrade-symfony-74

## Pull requests

Create a dedicated branch:

    git checkout -b feature/descriptive-name

Keep changes focused and include documentation when behavior changes.

Before opening a pull request:

- run Bash syntax validation
- run ShellCheck
- verify that no credentials or private data are included
- update CHANGELOG.md when appropriate
- update README.md when usage changes

## Commit messages

Clear conventional-style commit messages are encouraged.

Examples:

    feat: add target-version option
    fix: preserve existing security branches
    docs: clarify installation requirements
    test: add upgrade fixture
    security: strengthen repository validation

## Security issues

Do not publicly disclose security vulnerabilities in an issue.

Follow SECURITY.md instead.
