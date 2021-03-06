## ReKamp

[![License MIT](https://img.shields.io/badge/license-MIT-blue.svg?style=flat-square)](https://github.com/ReSwift/ReSwift/blob/master/LICENSE.md)
[ ![Download](https://api.bintray.com/packages/xorum-io/ReKamp/ReKamp/images/download.svg?version=1.0.5) ](https://bintray.com/xorum-io/ReKamp/ReKamp/1.0.5/link)

Port of [ReKotlin](https://github.com/ReKotlin/ReKotlin) to Kotlin Multiplatform, which corresponds to [ReKotlin/1.0.5](https://github.com/ReKotlin/ReKotlin/releases/tag/1.0.5). Supports **JVM**, **Android**, **iOS**.

## Introduction

This is an almost exact copy of [ReKotlin/1.0.5](https://github.com/ReKotlin/ReKotlin/releases/tag/1.0.5) with a few changes to source code and Gradle scripts to support Kotlin Multiplatform.

See official [ReKotlin](https://github.com/ReKotlin/ReKotlin) documentation for examples of usage in JVM / Android projects. Nothing has changed on these platforms. For usage in iOS projects, see the next section.

## Usage on iOS

[Kotlin Multiplatform](https://kotlinlang.org/docs/reference/multiplatform.html) allows the code written in Kotlin to run on any widely-used platforms. In case of iOS, Kotlin is compiled by [Kotlin/Native](https://kotlinlang.org/docs/reference/native-overview.html) to native code, which can be run without JVM.

You can even access libraries used in common Kotlin code from your iOS code written in Obj-C / Swift. There are a few limitation though, which change class / methods namings.

### Library prefix

Even though Swift has namespaces, we can't benefit from them when working with KMP. It happens because shared code is linked trough Obj-C header file.

To prevent collisions of class names from different libraries, Kotlin/Native is adding prefixes to any class name available in library. This prefix is used to be the library name.

In our case, it's `ReKamp` prefix. For example, `StoreSubscriber` becomes `ReKampStoreSubscriber`.

## Download

Add the repository to your project's `build.gradle`
```groovy
repositories {
    maven { url "https://dl.bintray.com/xorum-io/ReKamp" }
}
```

Following targets are available
```groovy
implementation "io.xorum:ReKamp:1.0.5"
implementation "io.xorum:ReKamp-jvm:1.0.5"
implementation "io.xorum:ReKamp-android:1.0.5"
implementation "io.xorum:ReKamp-iosX64:1.0.5"
implementation "io.xorum:ReKamp-iosArm32:1.0.5"
implementation "io.xorum:ReKamp-iosArm64:1.0.5"
```

Example of usage can be found here: https://github.com/xorum-io/codeforces_watcher/blob/dev/common/build.gradle
