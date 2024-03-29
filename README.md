<h1 align="center">
  EasyExternalDirectoryAndroid
</h1>

<div align="center">
    <a><img src="https://img.shields.io/badge/Version-2.2.1-brightgreen.svg?style=flat"></a>
    <a><img src="https://img.shields.io/badge/ID-gzeinnumer-blue.svg?style=flat"></a>
    <a><img src="https://img.shields.io/badge/Java-Suport-green?logo=java&style=flat"></a>
    <a><img src="https://img.shields.io/badge/Kotlin-Suport-green?logo=kotlin&style=flat"></a>
    <a href="https://github.com/gzeinnumer"><img src="https://img.shields.io/github/followers/gzeinnumer?label=follow&style=social"></a>
    <br>
    <p>Simple way to make <b>Directory</b>, <b>File</b>, and <b>Zip</b>.</p>
</div>

---
# Content List
* [Download](#download)
* [Feature List](#feature-list)
* [Tech stack and 3rd library](#tech-stack-and-3rd-library)
* [Example Code/App](#example-codeapp)
* [Version](#version)
* [Contribution](#contribution)

---
# Download
Add maven `jitpack.io` and `dependencies` in `build.gradle (Project)` :
```gradle
// build.gradle project
allprojects {
  repositories {
    ...
    maven { url 'https://jitpack.io' }
  }
}

// build.gradle app/module
dependencies {
  ...
  implementation 'com.github.gzeinnumer:EasyExternalDirectoryAndroid:version'

  // reactive
  implementation "io.reactivex.rxjava2:rxjava:2.1.9"
  implementation "io.reactivex.rxjava2:rxandroid:2.0.1"
  implementation('com.github.bumptech.glide:glide:4.7.1@aar') {
    transitive = true
  }
  implementation 'com.karumi:dexter:4.2.0'
  implementation 'com.squareup.picasso:picasso:2.71828'
  implementation "rebus:permission-utils:2.0.7"
}
```

---
# Feature List

This library need Permission you can use this step [**MultiPermission**](https://github.com/gzeinnumer/MultiPermition2) or use your own.

#### [Function Global Directory](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_1.md)
- [Create Folder](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_1.md#create-folder)
- [Is File Exists](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_1.md#is-file-exists)
- [Delete Folder](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_1.md#delete-folder)
- [Check Available Size In Storage](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_1.md#check-available-size-in-storage)

#### [Function Global File](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_2.md)
- [Create File](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_2.md#create-file)
- [Is File Exists](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_2.md#is-file-exists)
- [Delete File](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_2.md#delete-file)
- [Delete All File Inside Folder](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_2.md#delete-all-file-inside-folder)
- [Read File](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_2.md#read-file)
- [AppentText](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_2.md#appenttext)

#### [Function Global Zip](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_3.md)
- [Encode Base64/Md5 to Zip](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_3.md#base64-to-zip)

#### [Function Global Image Camera](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_4.md)
- [Take Image From Camera And Compress](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_4.md#take-image-from-camera-and-compress)

#### [Function Global Image Galery](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_5.md)
- [Take Image From Galery And Compress](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_5.md#take-image-from-galery-and-compress)

#### [Function Global Image Internet](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_6.md)
- [Download Image From Internet](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/README_6.md#download-image-from-internet)

#### File Picker Example
- [Sample Project](https://github.com/gzeinnumer/FilePickerExample)

---
# Tech stack and 3rd library
- MultiPermition ([docs](https://github.com/gzeinnumer/MultiPermition2))
- Androidwave ([docs](https://androidwave.com/))
- Glide ([docs](https://github.com/bumptech/glide))
- Picasso ([docs](https://github.com/square/picasso))
- Permissions ([docs](https://developer.android.com/guide/topics/permissions/overview))
- File ([docs](https://developer.android.com/reference/java/io/File))
- File Provider ([docs](https://developer.android.com/training/secure-file-sharing/setup-sharing?hl=id))
- Take Foto ([docs](https://developer.android.com/training/camera/photobasics?hl=id))
- Intent Galery ([docs](https://developer.android.com/guide/components/intents-common?hl=id))
- Android Internet ([docs](https://developer.android.com/training/basics/network-ops/connecting))
- RxJava/RxAndroid ([docs](https://github.com/ReactiveX/RxJava))
- Taphaelbussa PermissionUtils ([docs](https://github.com/raphaelbussa/PermissionUtils)) thanks to Rebus.

---

**Debug** if you find trouble and function doesn't work you can trace with this

| ![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/debug.jpg) |
|:-------------------------------------------------------------------------------|
| Example `Logcat`                                                               |

---
# Example Code/App

[Sample Code And App](https://github.com/gzeinnumer/MyLibDirectoryExample)

---
# Version
- **1.4.3**
  - First Release
- **1.5.0**
  - Add Feature Delete Dir or File
- **1.5.1**
  - More simple on take image galery
- **1.5.2**
  - Bug Fixing
- **1.5.3**
  - Bug Fixing
- **1.5.4**
  - All Callback Preload, Error and Message Status
- **1.5.5**
  - Bug Fixing
- **1.5.6**
  - Bug Fixing
- **2.0.0**
  - Support SDK 16
- **2.1.0**
  - Message Error CallBack
- **2.2.0**
  - Free Space Storage Checker
- **2.2.1**
  - Bug Fixed

---
# Contribution
You can sent your constibution to `branch` `open-pull`.

---

```
Copyright 2020 M. Fadli Zein
```
