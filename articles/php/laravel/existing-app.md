# Existing Laravel App
Part of what makes Nanobox so useful is you don't even need php or Laravel installed on your local machine to use them.

## Setup

#### cd into your Laravel app
Change into an existing project folder

```bash
cd my-laravel-app
```

**HEADS UP**: All `nanobox` commands *must* be run from within your project folder.

#### Add a boxfile.yml
Nanobox uses a <a href="https://docs.nanobox.io/boxfile/" target="\_blank">boxfile.yml</a> to configure your app's environment.

At the root of your project create a `boxfile.yml` telling Nanobox you want to use the PHP <a href="https://docs.nanobox.io/engines/" target="\_blank">engine</a>:

```yaml
run.config:
  # install php and associated runtimes
  engine: php

  # php engine configuration (php version, extensions, etc)
  engine.config:

    # sets the document root to public
    document_root: public

    # sets the php version to 7.1
    runtime: php-7.1

    # enables php extensions
    extensions:
      - pdo
      - mbstring
      - tokenizer
      - session
      - zip
      - dom
      - xml
      - ctype
      - xmlwriter
```

## Add a local DNS
Add a convenient way to access your app from the browser:

```bash
nanobox dns add local laravel.local
```

## Run the app

**HEADS UP**: If your app uses a database, you'll need to [add and configure it](/php/laravel/add-a-database) before your app will run.

To allow connections from the host machine into the app's container, you'll need to run your app so it listens on all available IP's (0.0.0.0).

```bash
nanobox run php artisan serve --host 0.0.0.0
```

Visit your app at <a href="http://laravel.local:8000" target="\_blank">laravel.local:8000</a>

## Explore
With Nanobox, you have everything you need develop and run your laravel app:

```bash
# drop into a Nanobox console
nanobox run

# where php is installed,
php -v

# your packages are available,
composer show

# and your code is mounted
ls

# exit the console
exit
```

## Now what?
Whats next? Think about what else your app might need and hopefully the topics below will help you get started with the next steps of your development!

* [Add a Database](/php/laravel/add-a-database)
* [Frontend Javascript](/php/laravel/frontend-javascript)
* [Local Environment Variables](/php/laravel/local-evars)
* [Back to Laravel overview](/php/laravel)
