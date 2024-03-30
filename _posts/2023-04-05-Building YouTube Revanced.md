# Why?

Now that Youtube Vanced has shut down, there isn't an easy way to enjoy the mods that came with it. But from its ashes,
we have something better in every way.

Youtube Revanced not only accomplishes what Vanced does, but allows you to do so with more customisablity and options,
if you know what you're doing.
If you pay for premium (or pay your favourite creators directly, if you don't like YouTube being in the middle), I
still think it's worthwhile since you'll get to enjoy features such as:

- Return Dislike counter
- More speed options (3x for crazy people like me)
- Sponsor Block
- and more!

However, I do hope you consider doing one of the two if you're sole purpose is to block ads!

The legality of downloading a pre-built version of Revanced is questionable, but building it yourself is completely fine
if you use your own copy, so let's get started!

To follow along I'd expect some basic knowledge in Android development + Linux.

## 1. Download Revanced Manager

There is also a CLI tool, but I found the Revanced manager to be a lot easier to work with.
You can download it from here: https://github.com/ReVanced/revanced-manager/releases

I recommend downloading a stable release from here.

Upon opening, you can go to the patches tab and see which version of Youtube is recommended for the current patches
supported. It's best to match of course, but I had no issues in the past using versions slightly newer or older.

If your phone is rooted and you already have Youtube installed, there is not much else to do but to follow the steps in
the app. If you don't have root, you'll need to continue forward to package your own Youtube apk in preparation for it
to be patched.

## 2. Find your own copy of YouTube APKs

The easiest way to do this is to extract the APK from your phone using apt. You'll be grabbing them as split packages,
but I'll show you how to combine them later on.

You'll need adb of course, which is part of
the [Android SDK](https://developer.android.com/tools/releases/platform-tools). You will also need developer mode turned
on with USB debugging turned on.

```bash
adb shell pm path com.google.android.youtube
```

A list of packages will show:

```
PS C:\Users\ryan9\Documents\flutter\android-sdk\platform-tools> .\adb.exe shell pm path com.google.android.youtube
package:/data/app/~~87t28bJOa-ZVyotaMLesXQ==/com.google.android.youtube-wuthuMnV6oxbS_dbxPJbZQ==/base.apk
package:/data/app/~~87t28bJOa-ZVyotaMLesXQ==/com.google.android.youtube-wuthuMnV6oxbS_dbxPJbZQ==/split_config.arm64_v8a.apk
package:/data/app/~~87t28bJOa-ZVyotaMLesXQ==/com.google.android.youtube-wuthuMnV6oxbS_dbxPJbZQ==/split_config.en.apk
package:/data/app/~~87t28bJOa-ZVyotaMLesXQ==/com.google.android.youtube-wuthuMnV6oxbS_dbxPJbZQ==/split_config.xxhdpi.apk
```

Download them all to a place on your PC:

```bash
adb pull /data/app/~~87t28bJOa-ZVyotaMLesXQ==/com.google.android.youtube-wuthuMnV6oxbS_dbxPJbZQ==/base.apk
adb pull /data/app/~~87t28bJOa-ZVyotaMLesXQ==/com.google.android.youtube-wuthuMnV6oxbS_dbxPJbZQ==/split_config.arm64_v8a.apk
# ... etc for the rest
```

## 3. Combine the APKs

Since the APKs are split, you'll need to combine them to use in Revanced Manager.

I found APKEditor to be the best tool for this. You can download it from here:
https://github.com/REAndroid/APKEditor/releases

```bash
java -jar APKEditor.jar m -i youtube_apks/
```

## 4. Patch the APK

You will now have a fresh APK ready for input to Revanced Manager. Simply upload onto your phone, and the rest should be
straight forward from the app.
Pick the patches you want and off your go!
