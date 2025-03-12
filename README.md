# [atet](https://github.com/atet) / [**_flutter_**](https://github.com/atet/flutter/blob/main/README.md#atet--flutter)

[![.img/logo_flutter.png](.img/logo_flutter.png)](#nolink)

# Quickest Flutter Setup Yet!

Want to start making apps and stop messing with troubleshooting Flutter installation? Look no further, get up and running in 10 minutes by just installing the bare-bones dependencies needed for Android mobile development with the Flutter development environment.

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

- This tutorial is only for Android mobile applications = less installs
- Tested in Windows 10 (I'm sure this works for Windows 11 too)
- Need fast internet for ~1.5 GB of file downloads
- No prior installations of:
   - Java for Windows
   - Android SDK
   - VSCode

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 1. Dependencies

### Java (OpenJDK)

- Given Oracle's change of heart with Java 8, we'll use OpenJDK instead
- Find the latest OpenJDK for Windows (x64) [here](https://learn.microsoft.com/en-us/java/openjdk/download#openjdk-21)
   - For example, you can directly download v21.0.6 from: https://aka.ms/download-jdk/microsoft-jdk-21.0.6-windows-x64.msi
- When installing, change the settings below to have `JAVA_HOME` and JavaSoft (Oracle) registry keys overwritten

### Android SDK ***without*** the entire Android Studio

- Find latest "Command line tools only" [here](https://developer.android.com/studio) (scroll all the way down)
   - For example, you can directly download v11076708 from: https://dl.google.com/android/repository/commandlinetools-win-11076708_latest.zip
- Extract this file in your Downloads folder
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

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 2. Installation

INSTALLATION.

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 3. Basic Examples

BASIC EXAMPLES.

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## 4. Next Steps

NEXT STEPS.

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## Other Resources

**Description** | **URL Link**
--- | ---
Android SDK without Android Studio | https://stackoverflow.com/a/42179456

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

## Troubleshooting

Issue | Solution
--- | ---
**"It's not working!"** | This concise tutorial has distilled hours of sweat, tears, and troubleshooting; _it can't not work_

[Back to Top](#table-of-contents)

----------------------------------------------------------------------------

<p align="center">Copyright © 2025-∞ Athit Kao, <a href="http://www.athitkao.com/tos.html" target="_blank">Terms and Conditions</a></p>