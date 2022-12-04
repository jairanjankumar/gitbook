# SBT

Use scalaz in REPL

```
set scalaVersion := "2.11.2"
set libraryDependencies += "org.scalaz" %% "scalaz-core" % "7.1.0"
set initialCommands += "import scalaz._, Scalaz._"
session save
console
```
