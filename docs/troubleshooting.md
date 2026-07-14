# Troubleshooting

## Command not found

Verify the link:

    ls -l "$HOME/bin/upgrade-symfony-74"

Verify PATH:

    printf '%s\n' "$PATH"

Add the directory to PATH:

    printf '\n%s\n' 'export PATH="$HOME/bin:$PATH"' >> "$HOME/.zprofile"

Open a new Terminal window.

## GitHub CLI is not authenticated

Run:

    gh auth login

Verify:

    gh auth status

## GitHub SSH authentication fails

Run:

    ssh -T git@github.com

Verify that your public SSH key is registered with GitHub.

## Repository contains uncommitted changes

Inspect the repository:

    git status --short

Commit, stash or discard those changes before running the upgrader.

## Composer cannot resolve dependencies

Review Composer's complete conflict report.

The application may contain packages that are not compatible with Symfony 7.4.

Useful commands:

    composer why-not symfony/framework-bundle 7.4.*
    composer prohibits symfony/framework-bundle 7.4.*

## No PHPUnit tests were found

This is a warning rather than an upgrade failure.

Add application tests before relying on automated upgrades for production systems.

## Abandoned package reported

An abandoned package is not automatically a security vulnerability.

Use this command to identify why it is installed:

    composer why PACKAGE-NAME

Plan its removal separately when appropriate.

## GitHub reports vulnerabilities after the branch is pushed

Dependabot reports default-branch status.

The alerts may remain until the pull request is merged into the default branch and GitHub completes rescanning.
