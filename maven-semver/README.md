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

Choose an unused `vMAJOR.MINOR.PATCH` tag. For example, to release the current
commit on GitHub's `main` as `v1.0.1`, run the following commands in this
repository.

```sh
git fetch origin
git tag -a v1.0.1 -m "Release maven-semver 1.0.1" origin/main
git push origin refs/tags/v1.0.1
```

In the repository's **Actions** tab, follow the **Maven SemVer Release** run for
the tag. A successful run publishes `v1.0.1` under **Releases** with
`maven-semver-1.0.1.jar` attached. A tag such as `v1.1.0-rc.1` publishes a
prerelease.

The release workflow also builds a Docker image from the release JAR on the
Actions runner without pushing it to a registry.
