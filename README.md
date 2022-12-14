# enumutil-kt ![Maven Central](https://img.shields.io/maven-central/v/io.github.materiiapps/enumutil?style=flat-square)

A Kotlin KSP plugin for generating repetitive functions for enums.

## Installation

```kt
plugins {
    id("com.google.devtools.ksp") version "1.7.22-1.0.8"
}

repositories {
    mavenCentral()
}

dependencies {
    implementation("io.github.materiiapps:enumutil:1.0.0")
    ksp("io.github.materiiapps:enumutil-ksp:1.0.0")
}

kotlin {
    sourceSets {
        getByName("main") {
            kotlin.srcDir("build/generated/ksp/main/kotlin")
        }
    }
}
```

## Usages

### @FromValue

Generate a `fromValue(...)` extension method for the target class.
This matches the first enum parameter and returns the matched enum value.

```kt
@FromValue
enum class OpCodes(val code: Int) {
    READY(1),
    DELETE(2),
    CREATE(3),
    DISCONNECT(4);

    companion object Serializer {
        // blah blah blah
    }
}

fun main() {
    val opCode = OpCodes.fromValue(1)
}
```
