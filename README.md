# mapBroke

1: set your mapbox token in the following locations:
  app.json - > "RNMapboxMapsDownloadToken"  
  or  
  App.js -> MapboxGL.setAccessToken('<YOUR_ACCESSTOKEN>');  

1: in package.json -> dependencies, make sure this exists:

        "@rnmapbox/maps": "rnmapbox/maps#main"

2: create a "local.properties" file in the /Android dir, put the following in it (path to android sdk, example is on a mac):  

        sdk.dir = /Users/[your macs user name]/Library/Android/sdk

3: in the gradle.build file in /Android, insert the text below in the "buildscript -> ext" section:  

        RNMapboxMapsImpl = "maplibre" // optinal - as this is the default

        RNMapboxMapsLibs = { // optional - only required if you want to customize it
            implementation ("org.maplibre.gl:android-sdk:9.5.2")
            implementation ("org.maplibre.gl:android-sdk-turf:5.9.0")

            implementation ("org.maplibre.gl:android-plugin-localization-v9:1.0.0")
            implementation ("org.maplibre.gl:android-plugin-annotation-v9:1.0.0")
            implementation ("org.maplibre.gl:android-plugin-markerview-v9:1.0.0")
        }

4: check that the "buildscript -> repositories" and "allprojects -> repositories" sections in your gradle.build match the ones in the build.gradle here

The following commands each give the error text below:

./gradlew build  
./gradlew syncReleaseLibJars  
./gradlew syncDebugLibJars

error text:

FAILURE: Build failed with an exception.

* What went wrong:
Execution failed for task ':expo-constants:createDebugExpoConfig'.
> Process 'command 'node'' finished with non-zero exit value 1
