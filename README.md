# ilume Camunda 7 to 8 Migration Tooling

This repository is a fork of the Camunda repository `camunda-7-to-8-migration-tooling`. It is intended to provide 
the artifacts for the Java Code conversion tools using the OpenRewrite recipes without the need of having access to 
the Camunda Enterprise Maven Repository. The OpenRewrite recipes to migrate the external tasks had to be removed 
from the build to prevent the need for Camunda Enterprise artifacts.

This respository is intended for training purposes only! To migrate production code use the standard Camunda 
migration tools.

To get rid of the Camunda Enterprise artifacts, some POM files had to be modified and some unit tests have been 
disabled (those for the External Tasks). The branches for those versions have the prefix `ilume`. The latest branch 
is `ilume/0.3.5`. Those branches are always based on the tags with the according version.

This repo provides to GitHub Maven Packages with the according artifacts:

```
<dependency>
  <groupId>io.ilume</groupId>
  <artifactId>camunda-7-to-8-code-conversion-recipes</artifactId>
  <version>0.3.5</version>
</dependency>
```
and

```
<dependency>
    <groupId>io.ilume</groupId>
    <artifactId>camunda-7-to-8-code-conversion-recipes</artifactId>
    <version>0.3.5</version>
</dependency>
```

One can see that the groupId has changed from `io.camunda` to `io.ilume`. The dependency of the `rewrite-maven-plugin` 
has to be adoped accordingly.

To use those artifacts, one needs to add the following repository entry to the POM file in which the OpenRewrite 
Maven plugin is executed:

```
  <pluginRepositories>
    <pluginRepository>
      <id>github</id>
      <name>ilume-Informatik-AG</name>
      <url>https://maven.pkg.github.com/ilume-Informatik-AG/ilume-camunda-7-to-8-migration-tooling</url>
    </pluginRepository>
  </pluginRepositories>
```
Additionally an entry has to be made to the Maven configuration file `settings.xml`:
```
</servers>
  <server>
    <id>github</id>
    <username>USERNAME</username>
    <password>ACCESS_TOKEN</password>
  </server>
</servers>
```
As the repository is public, it is sufficient to have any GitHub user create a classic accecss token with at least 
the permission `read:package`. 