# Building a MRJAR with Gradle

WARNING: Before doing this, we strongly recommend to read this [blog post](https://blog.gradle.org/mrjars) which highlights the consequences of your decision.

# Cross-compilation

By default, this build expects you to run on JDK 9. If you do, it will configure the various Java compilation tasks to use `--release` with the same level as their source compatibility level. In other words, the Java 8 source set will use `--release 8`, while the Java 9 source set will use `--release 9`. This will let each source set compile against the appropriate Java API.

If you don't run on JDK 9, then you will need to setup path to the various JDKs, using environment variables:

- `JAVA_8` must point to a valid JDK 8 installation
- `JAVA_9` must point to a valid JDK 9 installation

Then you need to run with `-PcrossCompile`, which will enable cross-compilation: compilation will be forked and each Java compile task will use the appropriate JDK.

