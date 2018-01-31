---
description: A tool for managing Ruby versions and dependencies. Similar idea to Python's virtualenv.
---

Ruby enVironment Manager

# Links

* [Installation/Home](https://rvm.io/)
* [Examples (much more expansive than mine)](https://rvm.io/workflow/examples)

# How-Tos

## Managing Rubies

_Install Specific Version_

```bash
$ rvm install ruby-2.5.0
```

_Download/compile ruby from HEAD (current dev/trunk version)_

```bash
$ rvm install ruby-2-head
```

## Managing Gemsets

Gemsets are the sets of Gems installed that are also coupled to the specific version(s) of Ruby installed. 

Each gemset is tied to a specific Ruby version, and delineated with the ruby version, the @ symbol, and then the name of the gemset. I.e. 2.5.0@gemset-name

Creating a gemset:

```bash
$ rvm gemset create <gemset-name>
```

Activating a gemset:

```bash
$ rvm use 2.5.0@gemset-name
```


