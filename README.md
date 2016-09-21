# SFML-AndroidStudio-Template
WIP. Android Studio, with the Gradle build system, template for a Native App with SFML

## Prerequisites
* Install Android Studio (2.2+)
* At the first startup of Android Studio install the SDK and NDK in Android Studio. I recommend doing it directly in android studio so your sdk and ndk directories are set correctly
* Install SFML for android (use gnustl_shared, otherwise you have to the change the build.gradle file in the template), have a look at the wiki there is a tutorial. By default the template will try to compile the app for *armeabi-v7a* and *armeabi*, you can change this behaviour in the build.gradle file (abiFilters), so you need to compile SFML for these too architectures, to use the template without changes to the abiFilters (Only release support at the moment).

## How to use
1. Clone this git, rename the folder and then just open it in android studio (2.2+)
2. Now you can simply run the application!
3. Replace the main.cpp with our own and put all the source files into the jni and subfolders, they will get compiled by "Gradle" automatically (do not remove the SFMLHack folder!)

## SFMLHack folder
Because SFML loads at startup the usercode as a shared lib, it's necessary that sfml-main (especially the function ANativeActivity\_onCreate) is present in the .so file. But this function does not get referenced by usercode therefore it will get stripped by the linker. With Ant we had the WHOLE\_STATIC\_LIB to tell the linker we need the whole lib, but this option (-Wl,--whole-archive) is not offered by the GradlePlugin yet. => We need to copy the essential headers into the project...
(There is a workaround with ldFlags but you would need to hardcode the platform, so we could only compile for one, so this isn't really an option)

## Todo
* Replace the SFMLHack folder, when WHOLE\_STATIC\_LIB is available in Gradle
* Support debug/release linking
* Maybe write a script to create the project with updated module application name

Don't forget to change the applicationId and moduleName in the app/build.gradle file or otherwise other SFML-Example projects will be in conflict with your shared-libs
