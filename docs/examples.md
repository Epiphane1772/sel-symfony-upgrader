# Examples

## Upgrade a repository

    upgrade-symfony-74 Epiphane1772/example-symfony-project

## Inspect the resulting pull request

    gh pr list --repo Epiphane1772/example-symfony-project

## View a pull request

    gh pr view --repo Epiphane1772/example-symfony-project --web

## Merge after review

Merging is intentionally outside the upgrader.

After validation and review:

    gh pr merge NUMBER --repo OWNER/REPOSITORY --merge --delete-branch

## Update the upgrader

    cd "$HOME/Projects/sel-symfony-upgrader"
    git checkout main
    git pull --ff-only origin main

The command installed through the symbolic link immediately uses the updated script.
