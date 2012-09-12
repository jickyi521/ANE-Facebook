Air Native Extension for Facebook (iOS + Android)
======================================

This is an [Air native extension](http://www.adobe.com/devnet/air/native-extensions-for-air.html) for [Facebook SDK](http://developers.facebook.com/docs/guides/mobile/) on iOS and Android. It has been developed by [FreshPlanet](http://freshplanet.com) and is used in the game [SongPop](http://songpop.fm).


Installation
---------

The ANE binary (AirFacebook.ane) is located in the *bin* folder. You should add it to your application project's Build Path and make sure to package it with your app (more information [here](http://help.adobe.com/en_US/air/build/WS597e5dadb9cc1e0253f7d2fc1311b491071-8000.html)).

On iOS:

* as explained [here](http://developers.facebook.com/docs/mobile/ios/build/), you will need to add some Info.plist additions in your application descriptor:
    
    ```xml
    <iPhone>
        
        <InfoAdditions><![CDATA[

            <key>CFBundleURLTypes</key>
            <array>
                <dict>
                    <key>CFBundleURLSchemes</key>
                        <array>
                            <string>fb{YOUR_FB_ID}</string>
                        </array>
                </dict>
            </array>

        ]]></InfoAdditions>

    </iPhone>
    ```

On Android:

* you will need to add the following activities and permission in your application descriptor:

    ```xml
    <android>
        <manifestAdditions><![CDATA[
            <manifest android:installLocation="auto">
                
                ...

                <uses-permission android:name="android.permission.INTERNET"/>
                
                ...

                <application>

                    ...
                    
                    <activity android:name="com.freshplanet.natExt.FBLoginActivity" android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen"></activity>
                    <activity android:name="com.freshplanet.natExt.FBDialogActivity" android:theme="@android:style/Theme.Translucent.NoTitleBar.Fullscreen"></activity>
                    <activity android:name="com.freshplanet.natExt.ExtendAccessTokenActivity"></activity>
                    
                </application>

            </manifest>
        ]]></manifestAdditions>
    </android>
    ```


Build script
---------

Should you need to edit the extension source code and/or recompile it, you will find an ant build script (build.xml) in the *build* folder:

    cd /path/to/the/ane/build
    mv example.build.config build.config
    #edit the build.config file to provide your machine-specific paths
    ant


Authors
------

This ANE has been written by [Thibaut Crenn](https://github.com/titi-us). It belongs to [FreshPlanet Inc.](http://freshplanet.com) and is distributed under the [Apache Licence, version 2.0](http://www.apache.org/licenses/LICENSE-2.0).