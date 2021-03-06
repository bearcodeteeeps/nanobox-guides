# Existing Echo App
Part of what makes Nanobox so useful is you don't even need Golang or Echo installed on your local machine to use them.

## Setup

#### cd into your Echo app
Change into an existing project folder:

```bash
cd my-echo-app
```

**HEADS UP**: All `nanobox` commands *must* be run from within your project folder.

#### Add a boxfile.yml
Nanobox uses a <a href="https://docs.nanobox.io/boxfile/" target="\_blank">boxfile.yml</a> to configure your app's environment.

At the root of your project create a `boxfile.yml` telling Nanobox you want to use the Golang <a href="https://docs.nanobox.io/enechoes/" target="\_blank">enechoe</a>:

```yaml
run.config:
  enechoe: golang
  enechoe.config:
    package: nanobox-echo
```

## Configure Echo

#### Listen on 0.0.0.0
To allow connections from the host machine into the app's container, your app needs to listen on all available IP's (0.0.0.0). Echo does this by default, and so no additional configuration is needed.

#### Add local DNS
Add a convenient way to access your app from the browser:

```bash
nanobox dns add local echo.local
```

## Run the app
**HEADS UP**: If your app uses a database, you'll need to [add and configure it](/golang/echo/add-a-database) before your app will run.

```bash
nanobox run go run server.go
```

Visit your app at <a href="http://echo.local:1323" target="\_blank">echo.local:1323</a>

## Explore
With Nanobox, you have everything you need develop and run your echo app:

```bash
# drop into a Nanobox console
nanobox run

# where golang is installed,
go version

# git is installed,
git --version

# and your code is mounted
ls

# exit the console
exit
```

## Now what?
Whats next? Think about what else your app might need and hopefully the topics below will help you get started with the next steps of your development!

* [Add a Database](/golang/echo/add-a-database)
* [Frontend Javascript](/golang/echo/frontend-javascript)
* [Local Environment Variables](/golang/echo/local-evars)
* [Back to Echo overview](/golang/echo)
