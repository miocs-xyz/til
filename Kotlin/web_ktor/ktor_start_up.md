# Start up to development a web application with ktor

## Install the gradle build tool
**Download it from [gradle-binary](https://services.gradle.org/distributions/gradle-6.8-bin.zip)**

Unzip the zip file, and set the bin path to environment variable

By Powershell
```powershell
[System.Environment]::SetEnvironmentVariable('Path', [System.Environment]::GetEnvironmentVariable('Path', [System.EnvironmentVariableTarget]::User) + ";path\to\gradle\bin", [System.EnvironmentVariableTarget]::User)
```

Then, restart powershell and test the gradle was install success.
```powershell
PS C:\Users\xxx> gradle -v

------------------------------------------------------------
Gradle 6.8
------------------------------------------------------------

Build time:   2021-01-08 16:38:46 UTC
Revision:     b7e82460c5373e194fb478a998c4fcfe7da53a7e

Kotlin:       1.4.20
Groovy:       2.5.12
Ant:          Apache Ant(TM) version 1.10.9 compiled on September 27 2020
JVM:          1.8.0_275 (Amazon.com Inc. 25.275-b01)
OS:           Windows 10 10.0 amd64
```

Make a folder to store the project. For example `ktorsample`
```powershell
PS D:\Workspace\kotlin> mkdir ktorsample

    Directory: D:\Workspace\kotlin

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
d----           1/16/2021 10:24 AM                ktorsample

PS D:\Workspace\kotlin>
```
Run `gradle init` to initial a new gradle project.
```powershell
PS D:\Workspace\kotlin> cd .\ktorsample\
PS D:\Workspace\kotlin\ktorsample> gradle init
Starting a Gradle Daemon, 1 incompatible and 1 stopped Daemons could not be reused, use --status for details

Select type of project to generate:
  1: basic
  2: application
  3: library
  4: Gradle plugin
Enter selection (default: basic) [1..4] 1

Select build script DSL:
  1: Groovy
  2: Kotlin
Enter selection (default: Groovy) [1..2] 2

Project name (default: ktorsample):

> Task :init
Get more help with your project: Learn more about Gradle by exploring our samples at https://docs.gradle.org/6.8/samples

BUILD SUCCESSFUL in 15s
2 actionable tasks: 2 executed
PS D:\Workspace\kotlin\ktorsample>
```

Now you can code for your first Ktor web application.

## Configure gradle with kotlin dsl
First, editor the **build.gradle.kts** and add the content follow.
```kotlin
import org.jetbrains.kotlin.gradle.tasks.KotlinCompile

group = "xyz.mioss"
version = "0.0.1-SNAPSHOT"

val ktorVersion = "1.5.0"

plugins {
    application
    kotlin("jvm") version "1.4.21"
}

repositories {
    mavenCentral()
}

java {
    sourceCompatibility = JavaVersion.VERSION_1_8
}

tasks.withType<KotlinCompile>().all {
    kotlinOptions.jvmTarget = "1.8"
}

dependencies {
    implementation("io.ktor:ktor-server-core:$ktorVersion")
    implementation("io.ktor:ktor-server-netty:$ktorVersion")
    implementation("ch.qos.logback:logback-classic:1.2.3")
}
```

Then make **src/main/kotlin** 
and **src/main/resources**
folder to store kotlin source files and configure file.

## Make the entrypoint to the web application.
1. Create a file named `application.conf` in **src/main/resources** to store the configure.
```
ktor {
    depolyment {
        port = 8080
    }

    application {
        modules = [ xyz.mioss.ktorsample.ApplicationKt.module ]
    }
}
``` 
2. Create a new kotlin file `Application.kt` to **src/main/kotlin** for storing the entry point list below. (Here, we use the embedded netty server.)
```kotlin
fun main(args: Array<String>): Unit = io.ktor.server.netty.EngineMain.main(args)
```
3. Return ***Hello, world***
, When access to the path /. With the minimal Ktor application. We need to import the objects listed bellow:

```kotlin
import io.ktor.application.*
import io.ktor.response.*
import io.ktor.routing.*
```
Then make a module to store routing.
```kotlin
fun Application.module() {
    routing {
        get("/") {
            call.respondText("Hello, world!")
        }
    }
}
```
## Define the mainClass to build.gradle.kts
Return to the **build.gradle.kts** and add the bellow code anywhere.
```kotlin
application {
    mainClass.set("io.ktor.server.netty.EngineMain")
}
```

## Execute server and access the home page.

Execute the server by command `gradle run`.

And access the [http://ocalhost:8080](http://ocalhost:8080), you will see the homepage below.

![Image](https://res.cloudinary.com/djjidnzay/image/upload/v1610772201/ktor-sample-home.png)