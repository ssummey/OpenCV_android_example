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

## OpenCV Camera Information
Add to android manifest file to allow camera permissions
```
<uses-permission android:name="android.permission.CAMERA"/> 
<uses-feature android:name="android.hardware.camera" android:required="false"/>
<uses-feature android:name="android.hardware.camera.autofocus" android:required="false"/>
<uses-feature android:name="android.hardware.camera.front" android:required="false"/>
<uses-feature android:name="android.hardware.camera.front.autofocus" android:required="false"/>
```
It is possible receive frames from the camera and have OpenCV process those frames. 
There are advantages and disadvantages to each, but the native camera view does allow a higher resoluiton.
In order to use the java camera view or the native camera view implement one of the following view classes
in a FrameLayout inside an xml activity file.
```
<FrameLayout xmlns:android=http://schemas.android.com/apk/res/android
     xmlns:tools=http://schemas.android.com/tools
     xmlns:opencv=http://schemas.android.com/apk/res-auto
     android:layout_width="match_parent"
     android:layout_height="match_parent" >

     <org.opencv.android.JavaCameraView
          android:layout_width="fill_parent"
          android:layout_height="fill_parent"
          android:visibility="gone"
          android:id="@+id/tutorial1_activity_java_surface_view"
          opencv:show_fps="true"  opencv:camera_id="any" />

     <org.opencv.android.NativeCameraView
          android:layout_width="fill_parent"
          android:layout_height="fill_parent"
          android:visibility="gone"
          android:id="@+id/tutorial1_activity_native_surface_view"
          opencv:show_fps="true"  opencv:camera_id="any" />

</FrameLayout>
```
### References
- OpenCV documentation `https://docs.opencv.org/`
- This guide uses information from Ancode's youtube videos `https://www.youtube.com/watch?v=psoeNfFAKL8`
 and `https://www.youtube.com/watch?v=2NUo2Up8JIM`
