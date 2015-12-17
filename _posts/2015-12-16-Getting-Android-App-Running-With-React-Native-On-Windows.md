---
published: true
layout: post
excerpt: "I managed to get a React Native (RN) hello world android app running in the android emulator on my windows machine and this post is going to describe some issues I faced and how solved those. So are you ready to get your hands dirty with some React Native (RN)?"
modified: {}
tags: 
  - ReactNative
  - Windows
comments: true
---


I managed to get a React Native (RN) hello world android app running from a windows machine and this post is going to describe some issues I faced and how to resolve them. So are you ready to get your hands dirty with some React Native (RN)?

1. Download [Android SDK for Windows](http://developer.android.com/sdk/index.html#Other) and install it.

2. Create a system variable called `ANDROID_HOME` and set the value to the SDK installation path. E.g: `C:\Users\UserName\AppData\Local\Android\android-sdk`. 
Make sure to select the required components when installing the SDK as indicated in [this](https://facebook.github.io/react-native/docs/android-setup.html) link. Also make sure to create a new virtual device in your emulator with the configuration mentioned in the above mentioned link. 

>Rapid Environemnt Editor makes handling environment variables a breeze in windows. Check out [Rapid Environment Editor](http://www.rapidee.com/en/about).

3. Once you have things in place, install the RN cli globally
> npm install -g react-native-cli

4. Create a new application by doind an Init as below
> react-native init HelloRN

5. Make sure to keep your emulator running or the phone connected. (Enable USB debugging in the phone as well)

6. Execute the following command from the application folder. This will try to build the project by fetching the dependencies. So be patient.
> react-native run-android

7. In windows the packager won't start automatically. So we have to start manually. Open another command promt and navigate to your application directory and execute the following command.
> react-native start

If you come accorss an error saying `ERROR Watcher took too long to load`, In your application directory open `\node_modules\react-native\packager\react-packager\src\FileWatcher\index.js` and increase the wait time to 50000 as `const MAX_WAIT_TIME = 50000;`

8. If things goes well you should see your application in the emulator or the device.

### Fixing 'Unable to download JS bundle' error 
When you open your app in the emulator/phone, you might see an error saying `Unable to download JS bundle`. This erro means the emulator/phone can't communicate to the packager to download the content.

The steps I followed to resolve this issues.
- Connect the phone to same WIFI network that your computer is connected to
- Get the IP of the machine using `ipconfig`
- Shake the device to bring the menu in your phone 
- Select `Dev Settings`
- Select `Debug server host for device`
- Provide the address as `<YourIp>:8081`
- Select `ReloadJS`

> executing the command `adb reverse tcp:8081 tcp:8081` is another option people were suggesting. You could try this as well. You can locate the `adb` exe under `<SDKInstallationDirectory>\Android\android-sdk\platform-tools`.

That should reload the content and your app should work.

If you are still having the issue, try to navigate to `localhost:8081/index.android.js` in your computer and see weather you get any results back. If this call failes, check weather port 8081 is used by some other application. You could use [TCPView](https://technet.microsoft.com/en-us/sysinternals/tcpview.aspx) to investigate the ports.