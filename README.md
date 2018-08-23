# Tonatona

[![Build Status](https://secure.travis-ci.org/arow-oss/tonatona.svg)](http://travis-ci.org/arow-oss/tonatona)
[![Hackage](https://img.shields.io/hackage/v/tonatona.svg)](https://hackage.haskell.org/package/tonatona)
[![Stackage LTS](http://stackage.org/package/tonatona/badge/lts)](http://stackage.org/lts/package/tonatona)
[![Stackage Nightly](http://stackage.org/package/tonatona/badge/nightly)](http://stackage.org/nightly/package/tonatona)

![tonatona](https://user-images.githubusercontent.com/1481749/38623497-c455af60-3de0-11e8-8683-a215d074e7e0.jpg)

## What is Tonatona?

Tonatona is a **meta** application framework. It handles lots of boring tasks
that are needed for real-world development such as reading in values
defined in environment variables, setting up logging, sending emails, accessing
databases, etc.

Tonatona can also be used with your favorite web framework as a meta web
application framework.  Tonatona **does not** provide the core functionalities
of web applications, such as routing, request parsing, response building, etc.
Instead, you can use plugins like `tonatona-servant`, `tonatona-spock`, or
`tonatona-yesod` to work with your favorite web framework.

Tonatona provides a plugin architecture so that anyone can add plugins
implementing arbitrary functionality.  This repository contains many standard
plugins that are helpful when writing Haskell applications.

## Goals for Tonatona

The most important goal of Tonatona is to make development speed fast and
maintenance cost low.

In the Haskell community, you often hear things like, "Haskell makes it easy to
maintain applications, but it takes a lot of time to create completely new,
production-ready applications."

Tonatona's goal is to change this to "Haskell is great to maintain big
applications, AND it is super-easy to create completely new, production-ready
applications!"

Tonatona achieves this goal by providing a plugin-based architecture.  There
are many production-ready plugins to use in your own code.  In order to start
using a new plugin, often all you have to do is just import it!  No need to
specify configuration from within your application.

## How to use Tonatona

(TODO)

## Available Plugins

Tonatona has many plugins available.  Here are the plugins provided in this repository.

*   [tonatona-db-postgresql](./tonatona-db-postgresql/README.md)

    [![Hackage](https://img.shields.io/hackage/v/tonatona-db-postgresql.svg)](https://hackage.haskell.org/package/tonatona-db-postgresql)
    [![Stackage LTS](http://stackage.org/package/tonatona-db-postgresql/badge/lts)](http://stackage.org/lts/package/tonatona-db-postgresql)
    [![Stackage Nightly](http://stackage.org/package/tonatona-db-postgresql/badge/nightly)](http://stackage.org/nightly/package/tonatona-db-postgresql)

    Provide access to a PostgreSQL database through the [persistent](http://hackage.haskell.org/package/persistent) library.

*   [tonatona-db-sqlite](./tonatona-db-sqlite/README.md)

    [![Hackage](https://img.shields.io/hackage/v/tonatona-db-sqlite.svg)](https://hackage.haskell.org/package/tonatona-db-sqlite)
    [![Stackage LTS](http://stackage.org/package/tonatona-db-sqlite/badge/lts)](http://stackage.org/lts/package/tonatona-db-sqlite)
    [![Stackage Nightly](http://stackage.org/package/tonatona-db-sqlite/badge/nightly)](http://stackage.org/nightly/package/tonatona-db-sqlite)

    Provide access to a SQLite database through the [persistent](http://hackage.haskell.org/package/persistent) library.

*   [tonatona-email-sendmail](./tonatona-email-sendmail/README.md)

    [![Hackage](https://img.shields.io/hackage/v/tonatona-email-sendmail.svg)](https://hackage.haskell.org/package/tonatona-email-sendmail)
    [![Stackage LTS](http://stackage.org/package/tonatona-email-sendmail/badge/lts)](http://stackage.org/lts/package/tonatona-email-sendmail)
    [![Stackage Nightly](http://stackage.org/package/tonatona-email-sendmail/badge/nightly)](http://stackage.org/nightly/package/tonatona-email-sendmail)

    Provide a way to easily send email directly by using `sendmail`.

*   [tonatona-environment](./tonatona-environment/README.md)

    [![Hackage](https://img.shields.io/hackage/v/tonatona-environment.svg)](https://hackage.haskell.org/package/tonatona-environment)
    [![Stackage LTS](http://stackage.org/package/tonatona-environment/badge/lts)](http://stackage.org/lts/package/tonatona-environment)
    [![Stackage Nightly](http://stackage.org/package/tonatona-environment/badge/nightly)](http://stackage.org/nightly/package/tonatona-environment)

    Provide a way to figure out at runtime whether we are in a `development`
    environment, `prodution` environment, or `testing` environment.

*   [tonatona-logger](./tonatona-logger/README.md)

    [![Hackage](https://img.shields.io/hackage/v/tonatona-logger.svg)](https://hackage.haskell.org/package/tonatona-logger)
    [![Stackage LTS](http://stackage.org/package/tonatona-logger/badge/lts)](http://stackage.org/lts/package/tonatona-logger)
    [![Stackage Nightly](http://stackage.org/package/tonatona-logger/badge/nightly)](http://stackage.org/nightly/package/tonatona-logger)

    Provide a way to log to the console at runtime using [monad-logger](http://hackage.haskell.org/package/monad-logger).

*   [tonatona-servant](./tonatona-servant/README.md)

    [![Hackage](https://img.shields.io/hackage/v/tonatona-servant.svg)](https://hackage.haskell.org/package/tonatona-servant)
    [![Stackage LTS](http://stackage.org/package/tonatona-servant/badge/lts)](http://stackage.org/lts/package/tonatona-servant)
    [![Stackage Nightly](http://stackage.org/package/tonatona-servant/badge/nightly)](http://stackage.org/nightly/package/tonatona-servant)

    Provide an easy way to run a [servant server](http://hackage.haskell.org/package/servant-server).

## Additional Features

Tonatona has the additional general features that apply to every plugin:

-   Make the end-user write a little boilerplate code up front in order to provide
    ease-of-use when writing their own business logic.

-   End users should be able to use many plugins without any configuration code
    or setup code.  Plugins should be configured to get configuration options
    from environment variables, command line flags, etc.  Plugins should be
    configured with reasonable defaults.

-   It should be possible to switch plugins just by rewriting the import statements.

    For instance, it should be possible to go from using `tonatona-db-sqlite` to
    `tonatona-db-postgresql` just by changing the import statement

    ```haskell
    import qualified Tonatona.Db.Sqlite as TonaDb
    ```

    to

    ```haskell
    import qualified Tonatona.Db.Postgresql as TonaDb
    ```

## Contributing

Information about contributing new plugins can be found in
[CONTRIBUTING.md](./CONTRIBUTING.md).

In general, new plugins will be accepted to Tonatona if they are widely useful.
For instance, a plugin adding support for a widely used database library will
probably be accepted, while a plugin adding support for a proprietary library
not widely used will probably not be accepted.

If your plugin is not accepted into this repository, you are free to support it
as a third-party repository, release it on Hackage, etc.  If you are using
Tonatona in a larger project, you will probably end up creating a few of your
own plugins!

## Maintainers

- [Kadzuya OKAMOTO](https://github.com/arowM)
- [Dennis Gosnell](https://github.com/cdepillabout)
