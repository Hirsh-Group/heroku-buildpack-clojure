# Heroku buildpack: Clojure with tools.deps

A version of the official Heroku Clojure buildpack but adapted to HGS needs.

## How it works

The buildpack will detect your app as Clojure if it has `deps.edn` file.
If your app needs a custom build step, it should specify it in the `HGS_CLJ_BUILD_ARGUMENTS`
environment variable (it will be run with `clj`) or in `bin/build` within the project.

## JDK Version

By default you will get OpenJDK 1.8. To use a different version, you
can commit a `system.properties` file to your app.

```sh-session
$ echo "java.runtime.version=11" > system.properties
$ git add system.properties
$ git commit -m "JDK 11"
```

## Troubleshooting

To see what the buildpack has produced, do `heroku run bash` and you
will be logged into an environment with your compiled app available.
From there you can explore the filesystem and run `clj` commands.
