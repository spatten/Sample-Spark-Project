# Sample Spark Project
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fspatten%2FSample-Spark-Project.svg?type=shield)](https://app.fossa.com/projects/git%2Bgithub.com%2Fspatten%2FSample-Spark-Project?ref=badge_shield)

Sample Spark project that may be compiled into a JAR for running via `spark-submit`.

## Dependencies
* Spark 2.10.5
* SBT 0.13.9

Both of these dependencies are available via [Homebrew](http://brew.sh/).

```bash
brew tap homebrew/versions
brew install scala210
brew install sbt
```

## Building
To build a JAR for submission via `spark-submit` use the `assembly` SBT task.

```bash
sbt assembly
```

## Helper Task
A custom task exists to both compile the JAR and submit it to the Spark cluster. It will need to be edited to point at your local `spark-submit` executable. This may be used within an IDE such as IntelliJ.

```scala
lazy val spark_run = taskKey[Unit]("Builds the assembly and ships it to the Spark Cluster")
spark_run := {
  ("/full/path/to/bin/spark_submit " + assembly.value) !
}
```


## License
[![FOSSA Status](https://app.fossa.com/api/projects/git%2Bgithub.com%2Fspatten%2FSample-Spark-Project.svg?type=large)](https://app.fossa.com/projects/git%2Bgithub.com%2Fspatten%2FSample-Spark-Project?ref=badge_large)