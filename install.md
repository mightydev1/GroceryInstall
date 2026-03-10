
# Mandatory Setup

View Categories

Table of Contents 

- [Run an existing flutter project on IDE​](../deliveryman-app/deliveryman-app-mandatory-setup.md)
- [Change App Logo​ and Icon](../deliveryman-app/deliveryman-app-mandatory-setup.md)
- [Change App Name​](../deliveryman-app/deliveryman-app-mandatory-setup.md)
- [Change Base URL​](../deliveryman-app/deliveryman-app-mandatory-setup.md)
- [Change App Package​](../deliveryman-app/deliveryman-app-mandatory-setup.md)
- [Setup Firebase for Push Notification​](../deliveryman-app/deliveryman-app-mandatory-setup.md)
- [Add Google Map API Key​](../deliveryman-app/deliveryman-app-mandatory-setup.md)

Setup Essentials

Requirements for Installation

**Admin & Web (V16.1)**

- PHP 8.2 or higher
- MySQL 5.7 or higher
- Laravel 12

**Mobile App (V16.1)**

- IDE: [Android Studio latest](https://developer.android.com/studio)
- Flutter SDK (version 3.41.1 Stable)
- Install [JDK 17](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
- Xcode 26.2 for IPA file build


## **Run an existing flutter project on IDE**[**​**](https://docs.6amtech.com/docs-demandium/mobile-apps/mandatory-setup#run-an-existing-flutter-project-on-ide) [#](../deliveryman-app/deliveryman-app-mandatory-setup.md)

To begin, it’s essential to verify that your **Flutter** and **Integrated Development Environment (IDE)** setup has been configured accurately

- Execute the command `flutter doctor` in your terminal. If any issues arise during this process, make sure to address and resolve them promptly.
- Then open your project. Once the project is open, Android Studio may prompt you to install the dependencies. If not, you can run the `flutter pub get` from the terminal in the project directory to fetch the dependencies.
- After the dependencies are installed, you should be able to run the app.

To change **App logo** and **App Icon** you need to follow these steps :

**App Logo :**

- Go to **<project>/assets/images/** and replace **logo.png** with your own logo.
- Go to **<project>/assets/images/** and replace **logo\_white****.png** for splash logo.
- Go to **<project>/assets/images/** and replace **logo\_with\_name.png** with your app bar logo.

**Note**

Please use the exact file name as described; otherwise, it will not work.

**App Icon :**

You can generate your app icon using this site [Visit](https://www.appicon.co)

- Then go to **/android/app/src/main/res** and replace all mipmap folders with your **<generated icon>/android** folder.
- Again go to **/ios/Runner** and replace **Assets.xcassets** with your generated **Assets.xcassets** folder.

## **Change App Name**[**​**](https://docs.6amtech.com/docs-demandium/mobile-apps/mandatory-setup#change-app-logo) [#](../deliveryman-app/deliveryman-app-mandatory-setup.md)

You need to set your app name in three different places.

- Go to **<project>/lib/util/app\_constrants.dart** and set the value of **appName**

```text
static const String appName = ‘YOUR_APP_NAME’;
```

```text
static const String appName = ‘YOUR_APP_NAME’;
```

- Change the value of **label** from **<project>/android/app/src/main/AndroidManifest.xml**

```text
android:label="YOUR_APP_NAME"
```

```text
android:label="YOUR_APP_NAME"
```

- Change the value of **CFBundleName** from **<project>/iOS/Runner/info.plist/iOS/Runner/info.plist**

```text
<key>CFBundleName</key>
<string>YOUR_APP_NAME</string>
```

```text
<key>CFBundleName</key>
<string>YOUR_APP_NAME</string>
```

## **Change Base URL**[**​**](https://docs.6amtech.com/docs-demandium/mobile-apps/mandatory-setup#change-base-url) [#](../deliveryman-app/deliveryman-app-mandatory-setup.md)

First you have to install your admin panel. For example: If your admin login url is **https://your\_domain.com/admin/auth/login** then the base url will be <https://your_domain.com>

- Open **<project>****/lib/util/app\_constrants.dart** and replace **baseUrl** variable value with your own URL.

Ensure that **don’t put slash(/)** at the end of your base url like

```text
static const String baseUrl = 'https://your_domain.com/';  
```

```text
static const String baseUrl = 'https://your_domain.com/';  
```

Put your base url like that –

```text
static const String baseUrl = 'https://your_domain.com'; 
```

```text
static const String baseUrl = 'https://your_domain.com'; 
```

## **Change App Package**[**​**](https://docs.6amtech.com/docs-demandium/mobile-apps/mandatory-setup#change-app-package) [#](../deliveryman-app/deliveryman-app-mandatory-setup.md)

First, you have to find out the existing package name/ namespace name. You can find it out from the top of the **android/app/build.gradle.kts** file. Now right-click on the project folder from Android Studio and click on replace in the path. You will get a popup window with two input boxes. In the first box, you have to put the existing package name that you saw in the **android/app/build.gradle.kts** file previously and write down your preferred package name in the second box and then click on the **Replace All** button.

## **Setup Firebase for Push Notification**[**​**](https://docs.6amtech.com/docs-demandium/mobile-apps/mandatory-setup#setup-firebase-for-push-notification) [#](../deliveryman-app/deliveryman-app-mandatory-setup.md)

First, you have to change your package name. If you didn’t, then follow [this](https://docs.6amtech.com/docs-stack-food/mobile-apps/mandatory-setup#change-app-package). Then have to create a Firebase project from [https://console.firebase.google.com](https://console.firebase.google.com/)

**WARNING**

Do not create multiple projects on your firebase console, if you have multiple apps like User App, Web, vendor App and delivery App. Create only one project and add multiple apps under the project.

**Android Setup :**

- Add an Android app under your firebase project with your own package name and app name.
- Click the **register app** button and download the **google-services.json** file from there.
- Copy that **google-services.json** file and go to your **<project>/android/app/** folder then delete the existing  **google-services.json** file and paste the **google-services.json** file that you downloaded**.**
- Create a totally white PNG logo for the notification icon. Paste it on **<project>/android/app/src/main/res/drawable/** and replace **notification\_icon.png** with your whiter version logo. Must keep the icon name **notification\_icon.png**

**IOS Setup :**

- Again add an app under the same project and download **GoogleService-Info.plist** and paste it under **<project>/iOS/ folder**. Also, follow this documentation for full setup for IOS: <https://firebase.flutter.dev/docs/messaging/apple-integration>

Paste the Firebase server key in the admin panel Notification Settings section. You can get the server key from Firebase project settings->Cloud Messaging->Server Key.

After your setup, please restart your IDE and uninstall your previously installed app then run it. Also, don’t try to test it on an emulator or simulator. Emulators and simulators are unable to get push. Use a real device in this case.

## **Add Google Map API Key**[**​**](https://docs.6amtech.com/docs-demandium/mobile-apps/mandatory-setup#add-google-map-api-key) [#](../deliveryman-app/deliveryman-app-mandatory-setup.md)

- You need to generate the google API key. Visit this link – <https://developers.google.com/maps/documentation/embed/get-api-key>
- You need to enable the mentioned APIs: Direction API, Distance Matrix API, Geocoding API, Maps SDK for Android, Maps SDK for iOS, Maps JavaScript API, Place API, Geolocation API, Routes API, Place API (New)
- You have to enable a billing account. Visit this url for activating: <https://support.google.com/googleapi/answer/6158867?hl=en>
- After generating the API key, you have to put it in 3 different places for Android, iOS and web.

**WARNING**

If your map key was generated before **March 1, 2025**, please make sure to newly enable the following APIs: **Routes API** and **Places API (New)**. All other settings can remain unchanged.

For android, open <project>/android/app/src/main/AndroidManifest.xml and place the value of com.google.android.geo.API\_KEY

- /android/app/src/main/AndroidManifest.xml

```text
<meta-data android:name="com.google.android.geo.API_KEY" android:value=“YOUR_MAP_API_KEY_HERE”/>
```

```text
<meta-data android:name="com.google.android.geo.API_KEY" android:value=“YOUR_MAP_API_KEY_HERE”/>
```

Open lib/utill/app\_constants.dart file

```text
static const String polylineMapKey = 'YOUR_MAP_KEY_HERE';
```

```text
static const String polylineMapKey = 'YOUR_MAP_KEY_HERE';
```

For iOS, open <project>/iOS/Runner/AppDelegate.swift and place the value of GMSServices.provideAPIKey

- /iOS/Runner/AppDelegate.swift

```text
GMSServices.provideAPIKey(“YOUR_MAP_API_KEY_HERE")
```

```text
GMSServices.provideAPIKey(“YOUR_MAP_API_KEY_HERE")
```
```markdown
## Android Signing Key Setup

Place the signing files in the following locations.

### Keystore File
```

android -> key -> key.jks

```

### Key Configuration File
```

android -> key.properties

```

### Example `key.properties`

```

storePassword=your_store_password
keyPassword=your_key_password
keyAlias=your_key_alias
storeFile=key/key.jks

```

```



## **Build for Android** [#](../user-app/user-app-build-release.md)

Run the following command to build the APK

```text
 flutter build apk --release
```
Run the following command to build appBundle

```text
 flutter build appbundle
```

Customisation




## **Country Code** [#](../user-app/user-app-customisation.md)

If you wish, the application will set your country code automatically in the login, register, address screen. To do this, just set up your country in the **Admin Panel > Business Settings**.

- Additionally, if you want to disable choosing another country code, then open your project and go to **<project>/lib/common/basewidget/custom\_textfield\_widget.dart** file and search **CodePickerWidget.** Now add a parameter with a value like this: enabled: false,

## **Language** [#](../user-app/user-app-customisation.md)

### **Add New Language** [#](../user-app/user-app-customisation.md)

If you want to add any new language then follow this steps:

- Go to **/assets/language** and press the right button on the language folder and create a new file and name it with your language code(.json). For example, if your language is Spanish, then you have to name your file as **es.json**. You have to name it with a proper and valid language code otherwise, the app won’t work. To get the language and country code, you can visit this URL: <https://docs.oracle.com/cd/E13214_01/wli/docs92/xref/xqisocodes.html>

- Copy all data from **en.json** and paste it into your created file.
- Translate all English text placed here after colon(:) to your expected language. Their texts are in key-value format. You have to translate the value only, not the key. Otherwise, it won’t work. For example: **“office”****:****“Office”**, -> **“office”**: **“Oficina”,**
- Add your country picture in the **<Project>/assets/images** folder. Must keep the file extension in png format. For example, **spanish.png**
- Go to **<Project>/lib/utils/images.dart** file**,** add a variablewith your country picture name. For example, if your added country picture name is **spanish.png**, then add a variable like -> static String get *spanish*=> ‘spanish’.png;
- Go to **<Project>/lib/utils/app\_constrants.dart** file, scroll down to the bottom and add one more **LanguageModel** under **the languages** array with your **imageUrl**, **languageName**, **countryCode** and **languageCode**. Again must remember that your language code and country code should be valid otherwise, the app won’t work

### **Remove Existing Language** [#](../user-app/user-app-customisation.md)

- If you wish to eliminate any currently present language, simply exclude the particular **LanguageModel** from the languages list.

### **Make Default Language** [#](../user-app/user-app-customisation.md)

- To set your language as the default language, place your **LanguageModel** at the first index of your language list.

Now uninstall your application from your devices and install it again.

## **Change App Color** [#](../user-app/user-app-customisation.md)

If you want to customize app theme color then follow these steps :

- Open the **<project>/lib/core/theme/light\_theme.dart file**. Set **primaryColor**, **primarycolorDark**, and other colors, and adjust them according to your preferences.
- In the same way for the dark theme, open the **<project>/lib/core/theme/dark\_theme.dart** file. Set **primaryColor**, **primaryColorDark**, and other colors, and adjust them according to your preferences.

## **Change App Font** [#](../user-app/user-app-customisation.md)

At , we use the **Ubuntu** font. However, if you want to change the app’s font, then follow these steps:

- Download your preferred font from the internet. Google has many free fonts you can check them: <https://fonts.google.com/>
- Unzip fonts and paste them to **<project>/assets/font/** folder.
- Mentioned them in **<project>/pubspec.yaml** file like

```text
fonts:
    - family: YOUR_FONT_FAMILY_NAME
      fonts:
        - assets/font/YOUR_FONT_FILE_NAME.ttf
          weight: YOUR_FONT_WEIGHT
```

```text
fonts:
    - family: YOUR_FONT_FAMILY_NAME
      fonts:
        - assets/font/YOUR_FONT_FILE_NAME.ttf
          weight: YOUR_FONT_WEIGHT
```

- Replace the font family name in the **<project>/lib/core/theme/light\_theme.dart**, **<project>/lib/core/theme/dark\_theme.dart**, and **<project>/lib/utils/styles.dart** files.

## **Change notification sound** [#](../user-app/user-app-customisation.md)

If you wish to change the notification sound for the web app and also for the Android app, then you need to follow these steps :

**Android App :**

- Go to **<project>/android/app/src/main/res/raw/notification.mp3** > notification.mp3 file. Replace this file with your desired ringtone file. Ensure that you do not change the filename. It must remain as **notification.mp3**

**Note**

Please use the exact file name as described; otherwise, it will not work.

## **Change onboarding text and graphics** [#](../user-app/user-app-customisation.md)

If you want to customize the onboarding title and content then follow these steps :

- Open **<project>/assets/language/en.json**. At the top, you will find texts with keys like **“on\_boarding\_1\_title” , “on\_boarding\_data\_1”**. Simply change the values without changing the keys. Repeat the same process for all languages.

```text
"on_boarding_title_one" :  "YOUR_PREFERRED_TITLE",
"on_boarding_title_two" :  "YOUR_PREFERRED_CONTENT",
"on_boarding_title_three" :  "YOUR_PREFERRED_TITLE,
```

```text
"on_boarding_title_one" :  "YOUR_PREFERRED_TITLE",
"on_boarding_title_two" :  "YOUR_PREFERRED_CONTENT",
"on_boarding_title_three" :  "YOUR_PREFERRED_TITLE,
```

- If you wish to update the graphics on the onboarding page, go to **<project>/assets/images/** and replace **onboard\_one.gif** and **onboard\_two.gif** with your preferred GIF files.

**Note**

Ensure that you use the same name and extension for your graphics. Otherwise, it will not work.


Problems

````markdown
# Kotlin Gradle Fix for Android / Flutter Projects

Fix Android build errors caused by deprecated Kotlin configuration and outdated Kotlin plugin versions.

---

## 1. Fix Deprecated `kotlinOptions`

Older Android projects configure the JVM target like this:

```kotlin
kotlinOptions {
    jvmTarget = JavaVersion.VERSION_11.toString()
}
````

This configuration is deprecated in newer Kotlin versions.

### Replace With

```kotlin
kotlin {
    compilerOptions {
        jvmTarget.set(org.jetbrains.kotlin.gradle.dsl.JvmTarget.JVM_11)
    }
}
```

### Example

**Before**

```kotlin
android {
    compileSdkVersion 34

    kotlinOptions {
        jvmTarget = JavaVersion.VERSION_11.toString()
    }
}
```

**After**

```kotlin
kotlin {
    compilerOptions {
        jvmTarget.set(org.jetbrains.kotlin.gradle.dsl.JvmTarget.JVM_11)
    }
}
```

---

# 2. Update Kotlin Plugin Version

Open:

```
android/settings.gradle
```

### Replace

```gradle
id("org.jetbrains.kotlin.android") version "OLD_VERSION" apply false
```

### With

```gradle
id("org.jetbrains.kotlin.android") version "2.3.10" apply false
```

---

# 3. Rebuild Project

Run:

```bash
flutter clean
flutter pub get
flutter build appbundle
```

or

```bash
flutter build apk
```

---

```
```
