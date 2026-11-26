# Maven SemVer

[![Maven SemVer CI](https://github.com/goranvasic/java/actions/workflows/maven-semver.yml/badge.svg?branch=main)](https://github.com/goranvasic/java/actions/workflows/maven-semver.yml)
[![Latest stable release](https://img.shields.io/github/v/release/goranvasic/java?display_name=tag&label=latest%20release)](https://github.com/goranvasic/java/releases/latest)

A Java 25 application that prints `Hello World` and exits.

## Build and run locally

Install JDK 25 and Maven 4. Set `JAVA_HOME` to the JDK directory and add the
JDK and Maven `bin` directories to your `PATH`. Run `mvn --version` to confirm
that Maven reports version 4.x and Java 25.

From the repository root, run the following commands.

```sh
cd maven-semver
mvn verify
java -jar target/maven-semver-1.0.0.jar
```

The local JAR defaults to version `1.0.0`, as set in [`pom.xml`](pom.xml).

## Build and run with Docker

Start Docker in Linux container mode, then run these commands from the
`maven-semver` directory.

```sh
mvn verify
docker build --tag maven-semver:local .
docker run --rm maven-semver:local
```

## Publish a GitHub release

Choose an unused `vMAJOR.MINOR.PATCH` tag. To release the current commit on
GitHub's `main`, run these commands with your chosen version in place of
`v1.2.0`.

```sh
git fetch origin
git tag -a v1.2.0 -m "Release maven-semver 1.2.0" origin/main
git push origin refs/tags/v1.2.0
```

In the repository's **Actions** tab, follow the **Maven SemVer Release** run for
the tag. For `v1.2.0`, the workflow pushes `ghcr.io/goranvasic/maven-semver:1.2.0`
and adds the image reference to the GitHub release notes. A tag such as
`v1.2.0-rc.1` publishes a prerelease and tags the image `1.2.0-rc.1`.
