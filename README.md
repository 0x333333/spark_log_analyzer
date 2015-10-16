# Introduction to Apache Spark in Java 8.

To compile this code, use maven:
```
$ mvn package
```

To run an example, such as LogAnalyzer, you can use spark-submit program
```
$  ${YOUR_SPARK_HOME}/bin/spark-submit
   --class "com.databricks.apps.logs.chapter1.LogAnalyzer"
   --master local[4]
   target/log-analyzer-1.0.jar
   apache.access.log
```

Or you can run the program in your IDE by setting a JVM Parameter
```
-Dspark.master=local[4]
```

Note: It is very helpful to set the log4j logging level to be WARN when
running these examples.

How to configure log4j logging level?

Under Spark home directory, run this command in the spark directory:

```
cp conf/log4j.properties.template conf/log4j.properties
```

Edit log4j.properties:

```
# Set everything to be logged to the console
log4j.rootCategory=INFO, console
log4j.appender.console=org.apache.log4j.ConsoleAppender
log4j.appender.console.target=System.err
log4j.appender.console.layout=org.apache.log4j.PatternLayout
log4j.appender.console.layout.ConversionPattern=%d{yy/MM/dd HH:mm:ss} %p %c{1}: %m%n

# Settings to quiet third party logs that are too verbose
log4j.logger.org.eclipse.jetty=WARN
log4j.logger.org.eclipse.jetty.util.component.AbstractLifeCycle=ERROR
log4j.logger.org.apache.spark.repl.SparkIMain"xprTyper=INFO
log4j.logger.org.apache.spark.repl.SparkILoop$SparkILoopInterpreter=INFO
```

Replace at the first line:

```
log4j.rootCategory=INFO, console
```

by

```
log4j.rootCategory=WARN, console
```

Save and restart your shell.
