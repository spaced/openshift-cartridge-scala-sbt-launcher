# OpenShift Scala, Spray and Akka

## Use it

Openshift environment:

```bash
rhc app create myscalaapp http://cartreflect-claytondev.rhcloud.com/reflect?github=juanpedromoreno/openshift-cartridge-scala
```

On git push, `sbt compile` will be called, then the script `start.sh` at the root of your repo will be called.

Example of `start.sh` script:

    #!/bin/bash
    sbt run com.example.Boot.main

Make sure `start.sh` is an executable file: `chmod +x start.sh` 

In your application listen on the environment variable $OPENSHIFT_SCALA_IP:$OPENSHIFT_SCALA_PORT

    interface = System.getenv("OPENSHIFT_SCALA_IP")
    port = System.getenv("OPENSHIFT_SCALA_PORT").toInt

This cartridge embed a [Akka persistence event sourcing](https://github.com/ScalaConsultants/akka-persistence-eventsourcing) example, but you could use any framework as long as sbt is used for compilation.

