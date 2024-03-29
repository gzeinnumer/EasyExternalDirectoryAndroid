<h1 align="center">
    EasyExternalDirectoryAndroid - Function Global Directory
</h1>

**CRUD Directory.** now we will make `Directory` with simple and fast.

This library need Permission you can use this step [**MultiPermission**](https://github.com/gzeinnumer/MultiPermition2) or use your own.

#
### Function Global Directory
> Example : FGDir.initExternalDirectoryName(valueString);

| Name                        | Return    | Parameter              | Description                                          |
|:----------------------------|:----------|:-----------------------|:-----------------------------------------------------|
| `initExternalDirectoryName` | `void`    | `String appFolder`     | Function to declare your own app folder on external  |
| `initExternalDirectoryName` | `void`    | `String appFolder`, `FGDir.MessageCallBack()`      | Function to declare your own app folder on external , and get message callback is error happen |
| `initFolder`                | `boolean` | `String... folderName` | Make folder in own app folder in external            |
| `isFileExists`              | `boolean` | `String path`          | To check is `directory` or `file` has created or not |
| `deleteDir`                 | `boolean` | `String path`          | To Delete `directory` or `file`                      |
| `getAvailableSpaceInKB`     | `long`    | `none`                 | Check available size in `KB`                         |
| `getAvailableSpaceInMB`     | `long`    | `none`                 | Check available size in `MB`                         |
| `getAvailableSpaceInGB`     | `long`    | `none`                 | Check available size in `GB`                         |
| `checkAvailableSpaceInKB`   | `boolean  | `long requestSize`     | Request empty storage with `KB`                      |
| `checkAvailableSpaceInMB`   | `boolean  | `long requestSize`     | Request empty storage with `MB`                      |
| `checkAvailableSpaceInGB`   | `boolean  | `long requestSize`     | Request empty storage with `GB`                      |

---
### Step 1. Enable Fitur.
Make Class `MyApp`, add 2 code on your `onCreate`. you need to declaration `External Folder Name` that you will use as you Folder Name in external. Now i am using `MyLibsTesting`.

```java
public class MyApp extends Application {

    @Override
    public void onCreate() {
        super.onCreate();

        String externalFolderName = getApplicationContext().getString(R.string.app_name); //MyLibsTesting

        //type 1
        FGDir.initExternalDirectoryName(externalFolderName);

        //type 2
        //if you want to trace the error tou can use this callback
        FGDir.initExternalDirectoryName(externalFolderName, new FGDir.MessageCallBack() {
            @Override
            public void messageError(String msg) {
                Toast.makeText(this, msg, Toast.LENGTH_SHORT).show();
            }
        });
    }
}
```
Add `MyApp` to manifest `android:name=".MyApp"`.
Manifest. add permission ke file manifest. I recommend to add `requestLegacyExternalStorage=true` if you using Android 10.
```xml
<?xml version="1.0" encoding="utf-8"?>
<manifest >

    <uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE" />
    <uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />

    <application
        android:name=".MyApp"
        android:requestLegacyExternalStorage="true"
        ...>

        ...

    </application>

</manifest>
```
**notes.** 
  - In this tutorial, i will put every file and folder in `/storage/emulated/0/MyLibsTesting`.

---
### Step 2. USE.
#### Create Folder
If you have granted your permission, Run function
`onSuccessCheckPermitions` inside `onRequestPermissionsResult`. **Only
Need 1 Time in FirstActivity** :

```java
public class MainActivity extends AppCompatActivity {

    ...

    private void onSuccessCheckPermitions() {
        // /storage/emulated/0/MyLibsTesting/folder1
        // /storage/emulated/0/MyLibsTesting/folder1/folder1_1
        // /storage/emulated/0/MyLibsTesting/folder2
        
        // String[] folders = {"/folder1","/folder1/folder1_1","/folder2"};
        String[] folders = new String[]{"/folder1","/folder1/folder1_1","/folder2"};
        
        if (FGDir.initFolder(folders)){
            Toast.makeText(this, "Folder sudah dibuat dan ditemukan sudah bisa lanjut", Toast.LENGTH_SHORT).show();
        } else {
            Toast.makeText(this, "Permition Required", Toast.LENGTH_SHORT).show();
        }
    }

    ...

}
```

#
#### is File Exists.

```java
boolean isExists = FGDir.isFileExists("/folder1");
```

#
#### Delete Folder.

```java
boolean isDeleted = FGDir.deleteDir("/folder1");
```

#
#### Check Available Size In Storage
```java
long sizeInKB = getAvailableSpaceInKB();
long sizeInMB = getAvailableSpaceInMB();
long sizeInGB = getAvailableSpaceInGB();
```
```java
boolean isSizeAvailable = checkAvailableSpaceInKB(60); //if free space more than 60KB return true
boolean isSizeAvailable = checkAvailableSpaceInMB(60); //if free space more than 60MB return true
boolean isSizeAvailable = checkAvailableSpaceInGB(60); //if free space more than 60GB return true
```

#
[FullCode](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/example/CreateFolder/MainActivity.java)

[Sample Code And App](https://github.com/gzeinnumer/MyLibDirectoryExample)

Preview :

|![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/example1.jpg)|![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/example2.jpg)|![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/example3.jpg)|![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/example4.jpg)|
|--|--|--|--|
|Request Permition |Folder MyLibsTesting created|`folder1` dan `folder2` created|`folder1_1` inside `folder1` has created|
