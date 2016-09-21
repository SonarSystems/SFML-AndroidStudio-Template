# SFML-AndroidStudio-Template
WIP. Android Studio, with the Gradle build system, template for a Native App with SFML

## How to use
1. Install SFML for Android (using the latest android NDK, i recommend gnustl\_shared, because c++\_shared/static is not working at the moment.
2. Clone this git, rename the folder and then just open it in android studio (2.2+)
3. Now you can simply run the application!

## SFMLHack folder
Because SFML loads at startup the usercode as a shared lib, it's necessary that sfml-main (especially the function ANativeActivity\_onCreate) is present in the .so file. But this function does not get referenced by usercode therefore it will get stripped by the linker. With Ant we had the WHOLE\_STATIC\_LIB to tell the linker we need the whole lib, but this option (-Wl,--whole-archive) is not offered by the GradlePlugin yet. => We need to copy the essential headers into the project...
(There is a workaround with ldFlags but you would need to hardcode the platform, so we could only compile for one, so this isn't really an option)

## Todo
* Replace the SFMLHack folder, when WHOLE\_STATIC\_LIB is available in Gradle
* Support debug/release linking
* Maybe write a script to create the project with updated module application name

Don't forget to change the applicationId and moduleName in the app/build.gradle file or otherwise other SFML-Example project will be in conflict with your shared-libs
