# merge-error-sample
Sample project to demonstrate an Android Studio bug.

Specifically it seems like Android Studio is not able to merge manifests
if a library module attempts to replace manifest parameters added by a 3rd party library.
This causes Android Studio to refuse building and deploying the application module.
However the project will build fine and generate the correct manifest when built directly from console.

## library-three
Is an example 3rd party library that includes an activity.
This must be published to maven local before the other modules in this project will work.
To publish to maven local execute `gradlew :library-three:publishToMavenLocal`.

## library-two
Is an example internal library that includes an activity

## library-one
Is an example internal library that includes the two other libraries,
and that attempts to override some parameters of the AndroidManifest from the two libraries.
It also contains the MainActivity that is expected to be used as launcher activity for the `app` module.

## app
Is an example app that only includes `library-one`.