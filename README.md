# SFML-AndroidStudio-Template
WIP. Android Studio, with the Gradle build system, template for a Native App with SFML

## How to use
1. Install SFML for Android (using the latest android NDK, i recommend gnustl\_shared, because c++\_shared/static is not working at the moment.
2. Clone this git, rename the folder and then just open it in android studio (2.2+)
3. Now you can simply run the application!


## Todo
* Replace the SFMLHack folder, when WHOLE\_STATIC\_LIB is available in Gradle
* Support debug/release linking
* Maybe write a script to create the project with updated module application name

Don't forget to change the applicationId and moduleName in the app/build.gradle file or otherwise other SFML-Example project will be in conflict with your shared-libs
