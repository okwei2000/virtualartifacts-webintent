# WebIntent Android Plugin for Cordova

## Why this fork
- Merge all changes from (https://github.com/cordova-misc/cordova-webintent). Feb.24, 2018
- I use this plugin to allow my cordova app to accept files (any files) from another app.
- I use this plugin to allow my cordova app to share files (any files) to another app.
- Change the onNewIntent() to process the Intent.EXTRA_STREAM (accepting files from other apps)
- Change the startActivity() to allow sharing any file using file://, using the FileProvider for Android N.
- I use it in my Phonegap Build project (https://build.phonegap.com)

## FileProvider on Android N. and above
Read more: https://inthecheesefactory.com/blog/how-to-share-access-to-file-with-fileprovider-on-android-nougat/en

You will need the following in AndroidManifest.xml
```xml
        <provider
            android:name="android.support.v4.content.FileProvider"
            android:authorities="com.yourcompany.provider"
            android:exported="false"
            android:grantUriPermissions="true">
            <meta-data
                android:name="android.support.FILE_PROVIDER_PATHS"
                android:resource="@xml/provider_paths" />
        </provider>
```
And provider_paths.xml in the res/xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<paths>
    <external-path
        name="external_files" path="." />
</paths>
```
If you aleady include some other plugins, like the camera plugin, those changes should have already in your project.

## Using Phonegap Build
Use either
```xml
    <plugin name="cordova-plugin-webintent2" spec="1.0.4" />
```
OR 
```xml
    <plugin spec="https://github.com/okwei2000/webintent.git" source="git" />
```

## Disclaimers
- I'm not an Android nor Cordova Plugin developer, I have little knowledge on how Android and the plugin works, especially Intent. I just made this plugin works for my own purpose. I just copy & pasted code from other plugins to make it work. If you know how to clean up the code, please let me know.

## History

- Originally [written](http://smus.com/android-phonegap-plugins/)
  by [Boris Smus](https://github.com/borismus)
  and published to
  [phonegap/phonegap-plugins](https://github.com/phonegap/phonegap-plugins/tree/DEPRECATED/Android/WebIntent)
  (now deprecated)

- Forked by [Rafael Agostini](https://github.com/Initsogar)
  and published to
  [Initsogar/cordova-webintent](https://github.com/Initsogar/cordova-webintent)
  (now removed)

- Forked by [Chris E. Kelley](https://github.com/chrisekelley)
  and published to
  [cordova-misc/cordova-webintent](https://github.com/cordova-misc/cordova-webintent)
  
- Forked by [Kevin] (https://github.com/okwei2000/webintent)
  to use for file sharing between apps and support Android N. & above with FileProvider.

- Many people forked but for some reason did not submit PRs,
  leaving their forks divergent.
  
## Licence ##

The MIT License

Copyright (c) 2010-2017 Boris Smus and contributors

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
