---
description: The web framework for perfectionists with deadlines.
---

# Project Startup (using vscode as IDE)

1. Using pipenv, install django: `pipenv install django`
1. Install helpful packages for dev: `pipenv install -d pylint pylint-django`
1. Enter the newly created virtualenv: `pipenv shell`
1. Start the Django project: `django-admin startproject mysite`
1. Open vscode in the project directory: `code .`
1. Edit the vscode settings file and add the following values:

```javascript
    {
        ...
        "python.linting.enabled": true,
        "python.linting.pylintEnabled": true,
        "python.linting.pylintArgs": [
            "--load-plugins=pylint-django"
        ],
        "python.linting.pylintPath": "<path to venv here>/bin/pylint"
    }
```

The path to the venv can be found with `pipenv --venv`.