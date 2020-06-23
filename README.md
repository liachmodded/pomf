# Yarn

Yarn is a set of open, unencumbered Minecraft mappings, free for everyone to use under the Creative Commons Zero license. The intention is to let 
everyone mod Minecraft freely and openly, while also being able to innovate and process the mappings as they see fit.

To see the current version being targeted, check the version in `build.gradle`!

## How important is yarn

Minecraft mappings is a fairly important but not required to Minecraft modding. It allows modders to modify Minecraft efficiently compared to directly looking at obfuscated code and guessing the functionalities.

It is not required to make a mod, and has nothing to do with running the game. Minecraft with fabric loader does not need yarn mappings at all; it only runs with [intermediary](https://github.com/FabricMC/Intermediary), another set of mappings that allows mods to preserve maximum compatibility between Minecraft updates.

## Usage
To use yarn-deobfuscated Minecraft for Minecraft modding or as a dependency in a Java project, you can use [loom](https://github.com/fabricmc/fabric-loom) Gradle plugin. See [fabric wiki tutorial](https://fabricmc.net/wiki/tutorial:setup) for more information.

In your fabric mod's `build.gradle`, in the `dependencies` block, change
```gradle
mappings "net.fabricmc:yarn:${project.yarn_mappings}:v2"
```
to
```gradle
mappings "com.github.liachmodded:yarn:${project.yarn_mappings}:v2"
```
and add
```gradle
repositories {
    maven { url = "https://dl.bintray.com/liachmodded/doublecart/" }
}
```
before the `dependencies` block.

A list of versions can be found on [the maven repo](https://dl.bintray.com/liachmodded/doublecart/com/github/liachmodded/yarn/). Replace the yarn
version listed in your `gradle.properties` accordingly.

There is [javadoc](https://liachmodded.github.io/yarn) available online as well. Feel free to dive into that.

To obtain a deobfuscated Minecraft jar, [`./gradlew mapNamedJar`](#mapNamedJar) will generate a jar named like `<minecraft version>-named.jar`, which can be sent to a decompiler for deobfuscated code.

## Contributing

Please remember that copying and pasting mappings from alternate projects under more restrictive licenses (such as MCP or Mojang's obfuscation maps)
is **completely forbidden** without explicit permission from the owners of said mappings to distribute the names under the CC0 license.
This includes using the names from those mappings for inspiration. Discussing the naming approaches used in said projects
is also not welcome - you have been warned. However, it is a good idea to consult name changes with other people - use pull requests or our community spaces to ask questions!

Please have a look at the [naming conventions](/CONVENTIONS.md) before submitting mappings.

### Getting Started

1. Fork and clone the repo
2. Run `./gradlew yarn` (Linux, macOS) or `gradlew yarn` (Windows)
3. Profit

## Gradle
Yarn uses Gradle to provide a number of utility tasks for working with the mappings.

### `yarn`
[`setupYarn`](#setupYarn) and download and launch the latest version of [Enigma](https://github.com/FabricMC/Enigma) automatically configured to use the merged jar and the mappings.

Compared to launching Enigma externally, the gradle task adds a name guesser plugin that automatically map enums and a few constant field names.

### `build`
Build a GZip'd archive containing a tiny mapping between official (obfuscated), [intermediary](https://github.com/FabricMC/intermediary), and yarn names ("named") and packages enigma mappings into a zip archive..

### `mapNamedJar`
Builds a deobfuscated jar with yarn mappings and automapped fields (enums, etc.). Unmapped names will be filled with [intermediary](https://github.com/FabricMC/Intermediary) names.

### `download`
Downloads the client and server Minecraft jars for the current Minecraft version to `.gradle/minecraft`

### `mergeJars`
Merges the client and server jars into one merged jar, located at `VERSION-merged.jar` in the mappings directory where `VERSION` is the current Minecraft version.

### `setupYarn`
[`download`](#download) and [`mergeJars`](#mergeJars)
