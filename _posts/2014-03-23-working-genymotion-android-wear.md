---
id: 603
title: Working with Genymotion and Android Wear
date: 2014-03-23T22:43:55+00:00
author: Joel
excerpt: "Google has released the Android Wear Developer Preview, which includes tools and APIs that allow developers to enhance their app notifications to provide an optimized user experience on Android wearable devices. The drawback is that preview is compatible with Android 4.3 and higher and is also not available for the Android emulator. This is a problem for developers who don't have a device running Android 4.3 or higher. However, with Genymotion you can overcome this problem and start to test the notifications on the Android Wear emulator."
layout: post
guid: http://www.joelifernandes.com/?p=603
permalink: /android/working-genymotion-android-wear/
dsq_thread_id:
  - "2492396971"
post_views_count:
  - "2765"
categories:
  - Android
tags:
  - Android
  - Android Wear
---
Google has released the Android Wear Developer Preview, which includes tools and APIs that allow developers to enhance their app notifications to provide an optimized user experience on Android wearable devices. The drawback is that the preview is compatible with Android 4.3 and higher and is also not available for the Android emulator. This is a problem for developers who don&#8217;t have a device running Android 4.3 or higher. However, with Genymotion you can overcome this problem and start to test the notifications on the Android Wear emulator.

  1. Download Genymotion for free <a href="https://cloud.genymotion.com/page/launchpad/download/" target="_blank">here</a>.
  2. Setup a Nexus 4 or Nexus 5 virtual device in Genymotion. 
      * Make sure you install Google Play Services on the Nexus device: 
          * Download the [zip](http://goo.im/gapps/gapps-jb-20130813-signed.zip) file
          * Drag it into the Nexus device
          * Reboot the device
  3. <span style="line-height: inherit;">Download the “Android Wear Preview” app.</span>
  4. Setup the Android Wear emulator &#8211; follow the instructions given <a href="http://developer.android.com/wear/preview/start.html#SetupApp" target="_blank">here</a>.
  5. Start both the Nexus and Android Wear emulator.  
<img class="aligncenter" alt="Android Wear Emulator" src="https://dl.dropboxusercontent.com/u/68257875/images/Android/wear-emulator.jpg" width="425" height="225" /> 
  6. Open the terminal or command prompt. Change your path to the _platform-tools _directory or execute this: 
    <pre>\path\to\adt-bundle\sdk\platform-tools\<strong>adb.exe devices
</strong></pre>
    
    This will show you the devices/emulators that are currently running</li> 
    
      * Execute this command to install the “Android Wear Preview” app on the Nexus emulator: 
        <pre>\path\to\adt-bundle\sdk\platform-tools\<strong>adb.exe -s [device name Nexus] install WearablePreview.apk </strong></pre>
    
      * Execute this command to forward port 5601 from the Nexus emulator, to receive the notifications on the Wear emulator: 
        <pre>\path\to\adt-bundle\sdk\platform-tools\<strong>adb.exe -s [device name Nexus] forward tcp:5601 tcp:5601</strong></pre>
    
      * Open the “Android Wear Preview” app on the Nexus device and Connect.
      * All done! You have now connected both the emulators and notifications should instantly start to appear on the Wear emulator.</ol> 
    
    [<a href="http://data-hk.com/rontam/Android_Wear_with_Genymotion/" target="_blank">via</a>]