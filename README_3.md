<h1 align="center">
    EasyExternalDirectoryAndroid - Function Global Zip
</h1>

**String Base64 ke Zip.** we will make file zip from Base64 dan extract it to your folder fast and simple.

This library need Permission you can use this step [**MultiPermission**](https://github.com/gzeinnumer/MultiPermition2) or use your own.

#
### Function Global Zip
> Example : FGZip.initFileFromStringToZipToFile(valueString, valueString, valueString, valueString, valueBoolean);

| Name                            | Return    | Parameter                                                                                                   | Description                                                          |
|:--------------------------------|:----------|:------------------------------------------------------------------------------------------------------------|:--------------------------------------------------------------------|
| `initExternalDirectoryName` | `void`    | `String appFolder`     | Function to declare your own app folder on external  |
| `initExternalDirectoryName` | `void`    | `String appFolder`, `FGDir.MessageCallBack()`      | Function to declare your own app folder on external , and get message callback is error happen |
| `initFileFromStringToZipToFile` | `boolean` | `String fileName, String zipLocation, String base64EncodeFromFile, String md5EncodeFromFile, boolean isNew` | Make file ZIP from Base64 and extract it to your destination folder |

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
#### Base64 To Zip

**Encode Base64/Md5 to Zip** Run function `onSuccessCheckPermitions` di
dalam `onRequestPermissionsResult`, make sure you have grant permission,
declaration variable :
1. `fileName` real file ZIP name.
2. `base64EncodeFromFile` from ZIP to Base64.
3. `md5EncodeFromFile` ZIP to Md5 to validate Base64 not corrupt.
4. `zipLocation` you extract will be in this folder.

Now execute the code :

```java
public class MainActivity extends AppCompatActivity {

    ...

    private void onSuccessCheckPermitions() {
        //   /storage/emulated/0/MyLibsTesting/ExternalBase64Md5ToZip.zip
        String fileName = "/ExternalBase64Md5ToZip.zip";

        //dari file zip diubah jadi base64
        //https://base64.guru/converter/encode/file
        String base64EncodeFromFile = "UEsDBBQAAAAIAJK6+FDfGqHQdAEAAABAAAAZAAAARXh0ZXJuYWxCYXNlNjRNZDVUb1ppcC5kYu3aQU7CQBQG4BlKgJJgWZh042JsQgIBTNQLiKYhRCgIJYqbZqRj0tgWgXIAbuQJvIk3MC516xRMhLowLiX/l2nmvXnpm25f0sFV24sEu5/MAh6xU1IklJIzxgghqnzS5Fs6kVPyO5UcHTwVZKDsPRPN03S5AQAAAAAAAPzRtZLR63U6jvidL3joziae6wQi4i6PeDJPX/TNhm0yu3HeNlmyysr+ZMx9wWzzxq70Uhm9WqWjVeP51JczsjMX04UIx8lU2WqbKJZDHoiazCrLfZrVSyW6fFj35MGjL5wfcWqrm7FZMlg5rxqea6gtyzabZp9ZXZtZw3a7Js/jiww1/vjN416/1Wn0R+zSHJXjV1ljaHdblrykY1p2JV9ZzebaC9HetVe5AQAAAAAAAMB/U1AUcti8FV5oLQIxy6UUosfZSY5+Rcfx/E+1NyIXAAAAAAAAAOyEIlVKdPOfAmU9/38QuQAAAAAAAABgt2RpShehMxx8AlBLAQI/ABQAAAAIAJK6+FDfGqHQdAEAAABAAAAZACQAAAAAAAAAgAAAAAAAAABFeHRlcm5hbEJhc2U2NE1kNVRvWmlwLmRiCgAgAAAAAAABABgAgEsYXNZh1gH+eSEy1mHWASKHEDLWYdYBUEsFBgAAAAABAAEAawAAAKsBAAAAAA==";

        //dari file zip diubah jadi md5
        //https://emn178.github.io/online-tools/md5_checksum.html
        String md5EncodeFromFile = "966af03a49f85b0df0afd3d9a42d0264";
        
        //   /storage/emulated/0/MyLibsTesting/zipLocation
        String zipLocation = "/zipLocation";
        //atau
        //   /storage/emulated/0/MyLibsTesting/
        //String zipLocation = "/"; // jika tidak mau diletakan dalam folder

        boolean overwriteExistingFiles =  true;

        //decode string menjadi file dan extrack ke tujuan zipLocation
        //   /storage/emulated/0/MyLibsTesting/zipLocation
        if (FGZip.initFileFromStringToZipToFile(fileName, zipLocation ,base64EncodeFromFile,md5EncodeFromFile, overwriteExistingFiles)){
            Toast.makeText(this, "Success load data", Toast.LENGTH_SHORT).show();
        } else {
            Toast.makeText(this, "Gagal load data", Toast.LENGTH_SHORT).show();
        }
    }
    
    ...

}
```
**notes.**
  - Make sure `fileName` is real name from file zip that you decode to Base64 and Md5.

#
[FullCode](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/example/EncodeBase64Md5toZip/MainActivity.java)

[Sample Code And App](https://github.com/gzeinnumer/MyLibDirectoryExample)

Preview :

| ![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/example2.jpg) | ![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/example7.jpg) | ![](https://github.com/gzeinnumer/EasyExternalDirectoryAndroid/blob/master/assets/example8.jpg)          |
|:----------------------------------------------------------------------------------|:----------------------------------------------------------------------------------|:-------------------------------------------------------------------------------------------|
| Folder `MyLibsTesting` created                                                    | `ExternalBase64Md5ToZip.zip` inside `MyLibsTesting` created from String Base64    | `ExernalBase64Md5ToZip.db` is the result of extract from file `ExternalBase64Md5ToZip.zip` |
