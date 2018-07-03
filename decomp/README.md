# Decompiled view

- Open IDEA
- Import main build.gradle as `File -> New -> Project from existing sources -> select build.gradle`
- Once imported, open the Gradle tool window
- Click the green + symbol
- Select the `decomp/build.gradle` file
- In the **Main** gradle project, run task `extractDecomp`
- Sources should appear in `decomp/src/main/java` and be ignored by git

You could also import only the decomp module as a project, but doing it the above way is necessary for the IDEA Mapping plugin.

## Decomp build.gradle

Mostly just a placeholder for now with the MC deps, just a plain old java project.