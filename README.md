# [atet](https://github.com/atet) / [**_flutter_**](https://github.com/atet/flutter/blob/main/README.md#atet--flutter)

[![.img/logo_flutter.png](.img/logo_flutter.png)](#nolink)

# Quickest Flutter Setup Yet!

*Want to stop messing with troubleshooting complex Flutter installations and start making apps?*

**Look no further!** Get up and running in 10 minutes by just installing the bare-bones dependencies needed for Android mobile development.

----------------------------------------------------------------------------

## Table of Contents

- [0. Requirements](#0-requirements)
- [1. Dependencies](#1-dependencies)
- [2. Installation](#2-installation)
- [3. Basic Examples](#3-basic-examples)
- [4. Next Steps](#4-next-steps)

### Supplemental

- [Other Resources](#other-resources)
- [Troubleshooting](#troubleshooting)

----------------------------------------------------------------------------

## 0. Requirements

- Unfortunately, there's no one-click install solution for this complex development environment
- This tutorial is only for Android mobile applications, which means less components
- Tested in Windows 10 (I'm sure this works for Windows 11 too)
- Need fast internet for ~1.5 GB of file downloads
- Do not have any prior installations of:
   - Java for Windows
   - Android SDK
   - VSCode

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 1. Dependencies

### Java (OpenJDK)

- Given Oracle's change of heart with Java 8, we'll use OpenJDK instead
- Find the latest OpenJDK for Windows (x64) [here](https://learn.microsoft.com/en-us/java/openjdk/download#openjdk-21) or you can directly download `v21.0.6` from: https://aka.ms/download-jdk/microsoft-jdk-21.0.6-windows-x64.msi
- Download through web browser and double-click the `*.msi` file to install
- During installation, change the settings below to have `JAVA_HOME` and JavaSoft (Oracle) registry keys overwritten

### Android SDK ***without*** the entire Android Studio

- Find latest "Command line tools only" [here](https://developer.android.com/studio) (scroll all the way down), or you can directly download `v11076708` from: https://dl.google.com/android/repository/commandlinetools-win-11076708_latest.zip
- Download through web browser and extract in Downloads
- Create the following directory structure: `C:\Android\SDK\cmdline-tools\latest`
- Within the `latest` directory, cut or copy all of the contents in the `cmdline-tools` directory from the unzipped file above
- Open Command Prompt and navigate to `C:\Android\SDK\cmdline-tools\latest\bin`

```cmd
> cd C:\Android\SDK\cmdline-tools\latest\bin
```

- Run (you must respond to license prompt):

```cmd
> sdkmanager --install "platform-tools" "platforms;android-30" "build-tools;30.0.3" "emulator" "system-images;android-30;google_apis;x86_64"
```

- Then run (you must respond to **several** license prompts):

```cmd
> sdkmanager --licenses
```

- Create an Android Virtual Device (AVD) but do not start it (must start emulation through VSCode)

```cmd
> avdmanager create avd -n my_avd -k "system-images;android-30;google_apis;x86_64" --device "pixel"
```

### Flutter SDK

- Find link to latest version of Flutter SDK [here](https://docs.flutter.dev/release/archive?tab=linux#stable-channel) (stable channel), or you can directly download `v3.29.1` from: https://storage.googleapis.com/flutter_infra_release/releases/stable/windows/flutter_windows_3.29.1-stable.zip
- Download through web browser and extract in Downloads
- Navigate into the extracted directory and move the `flutter` subdirectory to the `C:\Android` directory you made earlier
- Tell flutter where Android SDK is by running this in Command Prompt:

```
> cd C:\Android\flutter\bin
> flutter config --android-sdk "C:\Android\SDK"
```

- In the Start Menu, search for "environment" and open the "Edit the system environment variables" entry
- Click on "Environment Variables" in the bottom-right of the popup
- Under "User variables," highlight the "Path" entry and click on "Edit"
- In the popup, Click on "New" and add the path to `C:\Android\flutter\bin` here
- Click "OK" to close out all windows
- If you have Command Prompt or VSCode open, you must restart them for these changes to take effect

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 2. Setting up VSCode for Flutter

### VSCode

- Download and extract VSCode Portable [here](https://code.visualstudio.com/download) (i.e., the `*.zip` version), or you can directly download the latest version from: https://code.visualstudio.com/sha/download?build=stable&os=win32-x64-archive
- You can place this extracted directory anywhere you want, on your Desktop, in Program Files, etc.
- Create a new directory to store all your Flutter apps, let's create `C:\Android\Flutter Projects` for this tutorial
- Open VSCode by navigating to this extracted folder in File Explorer and executing `..\VSCode-win32-x64-1.98.1\Code.exe`
- On the top-left, click on Explorer (`CTRL+SHIFT+E`) and on "Open Folder" to set the current working directory to `C:\Android\Flutter Projects`
- VSCode will warn you about "trusted execution," reminding you that code you didn't write should be handled carefully

### Flutter Extension and Configuration

- On left-hand menu, choose Extensions (also, keyboard shortcut `CTRL+SHIFT+X`)
- Search for "Flutter"
- Install Flutter extension by Dart Code (may also install other extension dependencies like Dart)
- In the Command Palette (`CTRL+SHIFT+P`, it is **critical** to have the "`>`" character here), type "`> flutter`" and choose "`> Flutter: Run Flutter Doctor`"
- A popup in the bottom-right will ask about Flutter SDK, click on "Locate SDK" and point it to `C:\Android\flutter` and it will continue its diagnostic assessment
- A new pane will open at the bottom showing console output, you should have the following `[√]` marks:

```
[√] Flutter (REQUIRED)
[√] Windows Version (REQUIRED)
[√] Android toolchain (REQUIRED)
[X] Chrome (**Don't need this for Android Virtual Device emulation**)
[!] Visual Studio (**Don't need for AVD**)
[!] Android Studio (**Don't need for AVD**)
[√] Connected device (REQUIRED)
[√] Network resources (REQUIRED)
```

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 3. Default Application Test

### Create Default Application

- Now we can start a new project within your project folder, in the Command Palette, execute the following:
   - "`>Flutter: New Project`"
   - Choose "`Application`"
   - Select the current folder to create project in, "`C:\Android\Flutter Projects`"
   - Give the project a name or use default "`flutter_application_1`"
- This will take a few moments for Flutter to create the project

### Configure Device as Microsoft Edge Browser

- The default project has a simple working application, to build and run this application on our AVD, we need to **first successfully build it to the Microsoft Edge browser**
- In the Command Palette, run "`>Flutter: Select Device`"
- Then select "**Edge** edge - web"
- Click on the "`main.dart`" script and press `F5`, this will kick off the build and send the app over to a new Edge browser window
- This simple app is a counter that increments when you click on the bottom-right button, **cool!**
- Stop the app by pressing Stop (`SHIFT+F5`) in VSCode or by closing out the Edge window

### Building Default Application to AVD

- Now we will build and run this application on our AVD; in the Command Palette, run "`>Flutter: Select Device`"
- Then select "**Start my avd** mobile emulator&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Offline Emulators" which will boot up the AVD
- After the boot up sequence the AVD will show the home screen of the emulated phone, leave this open in the background
- Click on the "`main.dart`" script and press `F5`, this will kick off the build and send the app over to your AVD
- Now you've got the app running on a emulated Android phone, **magnificent!**
- Stop the app by pressing Stop (`SHIFT+F5`) in VSCode or by closing out the AVD window

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 4. Next Steps

The sky is the limit! You might want to learn how to build your project into an [Android Package Kit (APK)](https://stackoverflow.com/a/51682414) so that you can deploy to a physical phone.

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## Other Resources

**Description** | **URL Link**
--- | ---
Android SDK without Android Studio | https://stackoverflow.com/a/42179456
Build Flutter app to APK | https://stackoverflow.com/a/51682414

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## Troubleshooting

Issue | Solution
--- | ---
**"It's not working!"** | This concise tutorial has distilled hours of sweat, tears, and troubleshooting; _it can't not work_

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

<p align="center">Copyright © 2025-∞ Athit Kao, <a href="http://www.athitkao.com/tos.html" target="_blank">Terms and Conditions</a></p>