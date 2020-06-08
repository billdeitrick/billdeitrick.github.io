---
description: Resources for developing Masonite web apps.
---

# Getting started with Masonite and Pipenv

Since I like to keep my system Pythons as clean as possible, this is the "low tech" workaround for creating a Masonite project that uses pipenv...

1. Create a new directory in which the project should live
1. Enter the project directory, and run `pipenv --python #.#` where "#.#" is desired Python version
    * This lets pipenv create the virtualenv
1. Get a shell with the new directory's venv activated: `pipenv shell`
1. Install the Masonite CLI: `pipenv install masonite-cli`
1. Now, delete the project directory
1. Then, create the new project with craft: `craft new [project_name]`; be sure project_name matches whatever the new directory was called that you were working with in previous steps
1. Enter the directory, and create a lock file: `pipenv lock`
1. Install the masonite dependencies with craft (will use pipenv): `craft install`
1. And...you're off!

# Adding Authentication

1. Ensure database is setup; otherwise you can't save users
1. Scaffold the authentication system: `craft auth`
1. Create a new secret key and add to .env: `craft key -s`
1. Run db migrations to create the users table: `craft migrate`
1. You should now be able to run the dev server and register a test user

# Misc Helpful Tidbits

* `craft list` will display a list of all available commands

