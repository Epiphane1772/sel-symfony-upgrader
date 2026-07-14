# SEL Symfony Upgrader

SEL Consulting utility for upgrading Symfony applications to Symfony 7.4 LTS.

The command clones or updates a GitHub repository, creates a security branch, upgrades Composer dependencies, performs security and application checks, pushes the branch and creates a pull request.

It does not merge pull requests and does not deploy applications.

Installation commands:

    git clone git@github.com:Epiphane1772/sel-symfony-upgrader.git "$HOME/Projects/sel-symfony-upgrader"
    mkdir -p "$HOME/bin"
    ln -sf "$HOME/Projects/sel-symfony-upgrader/bin/upgrade-symfony-74" "$HOME/bin/upgrade-symfony-74"

Usage:

    upgrade-symfony-74 OWNER/REPOSITORY

Example:

    upgrade-symfony-74 Epiphane1772/api-idf.transports.express-v1.2
