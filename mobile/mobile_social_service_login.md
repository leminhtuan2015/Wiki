### Social Login Google
### Social Login Facebook
### Backend Firebase


------------------------------------------------------

* NOTICE For **Social Login**: 
  * **Android** : Google Login **NOT** need to add **google-services.json** to project
  * **IOS** : Google Login **NOT** need to add **GoogleService-Info.plist** to project
  
* NOTICE For **Backend Firebase**:

  * **Android** : Firebase do need add **google-services.json** to project
  * **IOS** :  Firebase do need add **GoogleService-Info.plist** to project

### Social Login Google

#### IOS (GoogleService-Info.plist, NOT need to add to Xcode project)
* On Server Create a Firebase Project
* On Firebase project create IOS app (Dont need the same bundle id with app)
* Get Client_ID from **GoogleService-Info.plist** (at Firebase console)
* Install Google SDK on project (Pod or add .framework to project)
* Set GG Client_ID in code at client
  ```swift
      GIDSignIn.sharedInstance().clientID = "1000219161365-8h5c1ff11i0992er41gvevjc6iqj50ma.apps.googleusercontent.com"
  ```
* Config Info/URL on setting
* Config openURL on AppDelegate
* Done

#### Android (google-services.json, NOT need to add to Android project ))

##### Case 1: (Default) need google-services.json  in you project
* On Server Create a Firebase Project
* On Firebase project create Android app
* Download and add **google-services.json** file to your project (YourProjectName/app/google-services.json)
* Install Google Service on project 
  * (compile 'com.google.android.gms:play-services-auth:11.8.0')
  * apply plugin: 'com.google.gms.google-services' from your app build.gradle

##### Case 2: NOT need google-services.json  in you project

* IF you do not want to add **google-services.json** you can config as below:

  * Deleting **apply plugin: 'com.google.gms.google-services' from your app build.gradle**
  * Deleting the google-services.json from your project
  * Removing the google-services plugin from your root build.gradle
  * Config code : (this make google not load default from google-services.json)
```java
    public static final String CLIENT_ID = "27075818457-79ejo179an04f7up29jdrp28nbr0tht7.apps.googleusercontent.com";
    public static final String CLIENT_SECRET = "LsAyDKUGccqYURXueUx9p2TZ";

    private static GoogleSignInOptions gso = new GoogleSignInOptions
            .Builder(GoogleSignInOptions.DEFAULT_SIGN_IN)
            .requestIdToken(CLIENT_ID)
            .requestServerAuthCode(CLIENT_ID)
            .requestEmail()
            .build();
```


### Social Login Facebook

#### IOS (Config Facebook ID in info.plist)
* On Facebook Develop create a Facebook App
* Make app is live + Enable Single Sign On for Your App
* Copy XML contain Facebook ID to **info.plist**
* Install Facebook SDK on project (Pod or add .framework to project)
* Config Info/URL on setting
* Config openURL on AppDelegate
* Done

```xml
<!-- Facebook ID to **info.plist** -->

<key>FacebookAppID</key>
	<string>1118793734903549</string>
	<key>FacebookDisplayName</key>
	<string>Fujigame</string>
	<key>LSApplicationQueriesSchemes</key>
	<array>
		<string>fbapi</string>
		<string>fb-messenger-api</string>
		<string>fbauth2</string>
		<string>fbshareextension</string>
	</array>
```

#### Android (Config Facebook ID in AndroidManifest.xml)
* On Facebook Develop create a Facebook App
* Make app is live + Enable Single Sign On for Your App
* Set **facebook_app_id** in AndroidManifest.xml.
* Install Facebook SDK on project : (compile 'com.facebook.android:facebook-android-sdk:4,5)'
* Provide the Development and Release Key Hashes for Your App

```xml
<!-- Facebook ID to **AndroidManifest.xml** -->
  <meta-data android:name="com.facebook.sdk.ApplicationId" android:value="@string/facebook_app_id"/>
```







