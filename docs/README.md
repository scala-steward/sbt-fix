# SBT plugin that enhances scalafix & scalafmt duo

[![][github-action-badge]][github-action] [![][maven-badge]][maven] [![][steward-badge]][steward]  [![][mergify-badge]][mergify]

> :exclamation: This project no longer enables synchronizing configuration across repositories. To enable that functionality, please check [alejandrohdezma/sbt-scalafix-defaults](https://github.com/alejandrohdezma/sbt-scalafix-defaults) and [alejandrohdezma/sbt-scalafmt-defaults](https://github.com/alejandrohdezma/sbt-scalafmt-defaults).
>
> If you want to provide your own organization's configuration you can use the previous repositories as templates and edit the `.scalafix.conf` and `.scalafmt.conf` at will.

```scala mdoc:toc
```

## Installation

Add the following line to your `plugins.sbt` file:

```sbt
addSbtPlugin("com.alejandrohdezma" %% "sbt-fix" % "@VERSION@")
```

## Usage

All included plugins are automatically activated, so you don't have to do anything to start using them.

### Running scalafix in all configurations

This plugin adds a `scalafixAll` new command that runs `scalafix` in all available configurations:

```sbt
scalafixAll
```

Also, this command accepts the same arguments as `scalafix`, so we can:

```sbt
// Execute a single rule
scalafixAll DisableSyntax

// Check without altering files
scalafixAll --check

// Insert /* scalafix:ok */ suppressions instead of reporting linter errors.
scalafixAll --auto-suppress-linter-errors
```

> For all the other possible arguments, refer to [scalafix docs](https://scalacenter.github.io/scalafix/docs/users/installation.html#help)

### Running both scalafix & scalafmt in a single command

This plugin also enables a `fix` command to every project in the build.

This command can be used to launch both `scalafmt` and `scalafix` in all supported configurations.

```sbt
fix
```

It can also be used for checking that all files have been fixed with both tools, exiting with non-zero code on violations, by appending the `--check` argument.

```sbt
fix --check
```

Which can be used in CI to check formatting easily.

[github-action]: https://github.com/alejandrohdezma/sbt-fix/actions
[github-action-badge]: https://img.shields.io/endpoint.svg?url=https%3A%2F%2Factions-badge.atrox.dev%2Falejandrohdezma%2Fsbt-fix%2Fbadge%3Fref%3Dmaster&style=flat

[maven]: https://search.maven.org/search?q=g:%20com.alejandrohdezma%20AND%20a:sbt-fix
[maven-badge]: https://maven-badges.herokuapp.com/maven-central/com.alejandrohdezma/sbt-fix/badge.svg?kill_cache=1

[mergify]: https://mergify.io
[mergify-badge]: https://img.shields.io/endpoint.svg?url=https://gh.mergify.io/badges/alejandrohdezma/sbt-fix&style=flat

[steward]: https://scala-steward.org
[steward-badge]: https://img.shields.io/badge/Scala_Steward-helping-brightgreen.svg?style=flat&logo=data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAA4AAAAQCAMAAAARSr4IAAAAVFBMVEUAAACHjojlOy5NWlrKzcYRKjGFjIbp293YycuLa3pYY2LSqql4f3pCUFTgSjNodYRmcXUsPD/NTTbjRS+2jomhgnzNc223cGvZS0HaSD0XLjbaSjElhIr+AAAAAXRSTlMAQObYZgAAAHlJREFUCNdNyosOwyAIhWHAQS1Vt7a77/3fcxxdmv0xwmckutAR1nkm4ggbyEcg/wWmlGLDAA3oL50xi6fk5ffZ3E2E3QfZDCcCN2YtbEWZt+Drc6u6rlqv7Uk0LdKqqr5rk2UCRXOk0vmQKGfc94nOJyQjouF9H/wCc9gECEYfONoAAAAASUVORK5CYII=