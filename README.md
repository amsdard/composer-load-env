Composer Load ENV
===

Simple handler to inject custom environment variables into composer scripts by load defined ENV files

Usage
---

* install library
```
composer require amsdard/composer-load-env
```

* add ENV files into `composer.json` as `extra.env-files` param
```
{
    ...
    "extra": {
        ...
        "env-files": [
            "FILE-PATH-1",
            "FILE-PATH-2"
        ],
    }
}
```

* add `load-env-files` script info Your `compoer.json`
```
{
    ...
    "scripts": {
        "load-env-files": [
            "Amsdard\Component\\EnvHandler::loadEnvFiles"
        ],
    },
    ...
}
```

* use `@load-env-files` in other scripts
```
{
    ...
    "scripts": {
        "post-install-cmd": [
            "@load-env-files",
            "@symfony-scripts"
        ],
        ...
    },
    ...
}
```

Workflow
---
* `@load-env-files` script will load files defined at `extra.env-files` param
* environment variables from files will be available in the current script scope