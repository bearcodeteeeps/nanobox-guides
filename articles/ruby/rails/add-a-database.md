# Add a Database

## Configure
You can add a database to your app by simply adding a data component to your `boxfile.yml`:

<div class="meta" data-class="snippet" data-optional-components="postgres,mysql,mongo" ></div>

<!-- <div class="meta" data-class="snippet" data-snippet-toggler="postgres,mysql,mongo" ></div> -->

In the above snippet `db` is the unique identifier of this component. It can be anything you choose as long as it is unique.

Nanobox generates the following environment variables based off that name:

* `DATA_DB_HOST` : auto-generated unique host ip
* `DATA_DB_USER` : user to connect with
* `DATA_DB_PASS` : unique password

For databases that require a name, the name will always be `gonano`.

**HEADS UP**: The next time you `nanobox run` your database will be provisioned.

## Connect
You can choose from any number of different database to add to your app. This example will show you a basic configuration for postgres.

Modify your `config/database.yml` to connect your app:

<div class="meta" data-class="configFile" data-run="config/database.yml"></div>

```yaml
default: &default
  adapter: postgresql
  encoding: unicode
  pool: 5
  timeout: 5000
  host: <%= ENV['DATA_DB_HOST'] %>
  username: <%= ENV['DATA_DB_USER'] %>
  password: <%= ENV['DATA_DB_PASS'] %>

development:
  <<: *default
  database: development

test:
  <<: *default
  database: test

production:
  <<: *default
  database: production
```

**HEADS UP**: Any database created by nanobox will *always* be named `gonano`

#### Update dependencies
Make sure your `Gemfile` has all the necessary dependencies for the database you're using. For postgres the following gems have been added:

```ruby
gem "pg"
```

Run `nanobox run bundle install` to install any new gems.

## Test

#### From an external client
You can connect directly to your database from an <a href="https://docs.nanobox.io/data-management/managing-local-data/" target="\_blank">external client</a>.

#### From Rails
Your can also test the connection with rails:

```bash
nanobox run rake db:setup
```

## Now what?
Whats next? Think about what else your app might need and hopefully the topics below will help you get started with the next steps of your development!

* [Frontend Javascript](/ruby/rails/frontend-javascript)
* [Local Environment Variables](/ruby/rails/local-evars)
* [Back to Rails overview](/ruby/rails)
