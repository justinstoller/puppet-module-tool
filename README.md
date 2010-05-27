puppet-module-site
==================

This is a Rails application that provides a website and web service for publishing, findiing and downloading Puppet modules.

Setup
-----

1. Run `sudo gem install less`
2. Install gems the Rails application depends on:
    * For development: Run `sudo rake RAILS_ENV=test gems:install`
    * For production: Run `sudo rake gems:install`
3. Run `rake setup` to create the required directories and these files using sensible defaults: `config/database.yml`, `spec/spec.opts` and `spec/rcov.opts`.
4. Customize the above files if you'd like, but do not check them into the repository.
5. Create the database using your database's tools or using these tasks:
    * For development: Run `rake db:create`
    * For production: Run `rake RAILS_ENV=production db:create`
6. Create the database tables:
    * For development: Run `rake db:migrate db:test:prepare`
    * For production: Run `rake RAILS_ENV=production db:migrate`

Secrets
-------

This application needs you to provide it with secret information such as a session encryption key. It will run with insecure settings by default to make it easy to get started, but will warn you each time it's started. These default settings include publicly-known cryptographic keys that will let anyone gain administrator privileges on your application. To secure your application and configure these secrets, create a `config/secrets.yml` file with your secret settings based on the instructions in the `config/secrets~sample.yml` file.

Environmental variables
-----------------------

You can alter the behavior of the application by setting environmental variables:

* Caching is enabled in the `production` and `preview` environments, but you can disable it with `CACHE=0`. To enable caching in the `development` and `test` environments, use `CACHE=1`.
* [New Relic](http://newrelic.com/) profiling and monitoring is enabled in the `production` and `preview` environments if a `config/newrelic.yml` file is found (a sample is provided at `config/newrelic~sample.yml`), but you can disable it with `NEWRELIC=0`. To enable New Relic in the `development` and `test` environments, create the configuration file and use `NEWRELIC=1`.

You can set these environmental variables easily from the command-line like this:

    CACHE=1 NEWRELIC=1 ./script/server