# Instructions for installing OpenCV on Android Studio

## Assumptions
This guide assumes Android Studio Version `2020.3.1` and OpenCV version `4.5.4`. Other versions of 
OpenCV may also work. Either create a new Android Studio project or follow this guide to add OpenCV to 
an existing Android application.

## Download OpenCV
Update the app build.gradle file (not the project) by adding `applicationId "opencv.org" ` in the `default config`
section. If any dependencies are highlighted yellow, accept Android Studio's suggested version. 
Note: When making changes to gradle files, complete a project sync after each change to ensure no build
errors.

## Add OpenCV Module to Android Studio
With this version of Android Studio importing the module directly doesn't work. Download the android
release for the OpenCV version from `https://opencv.org/releases/`. Unzip the OpenCV download and copy
the sdk folder to the root project directory.

Edit the setting.gradle file, and add `include :sdk` to the file.

Next follow these steps:
```
1) Select the `file` menu
2) Select `project structure` from the menu
3) Select `dependencies` and select `app` in the modules pane
4) Click add dependencies `+` and then `module dependencies`
5) Select `sdk` from the available choices and click ok to exit
```

Next follow these steps:
```
1) Select the `file` menu
2) Select `project structure` from the menu
3) Select `modules` and select `sdk` in the modules pane
4) Set compile version to API 26 and build tools version to 30.0.3
```

### References
OpenCV documentation `https://docs.opencv.org/`
This guide uses information from Ancode's youtube video `https://www.youtube.com/watch?v=psoeNfFAKL8`

