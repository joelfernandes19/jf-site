---
id: 634
title: Connecting Android with ADB over Wi-Fi (TCP/IP)
date: 2014-06-20T18:36:12+00:00
author: Joel
excerpt: Generally developers connect their Android devices to their development system or computer via a USB cable in order to install/debug applications and for other purposes of course. However, you can also perform all these by connecting your device via a common Wi-Fi network.
layout: post
guid: http://joelifernandes.com/?p=634
permalink: /android/connecting-android-adb-over-wifi-tcpip/
dsq_thread_id:
  - "2781122966"
post_views_count:
  - "570"
categories:
  - Android
---
Generally developers connect their Android devices to their development system or computer via a USB cable in order to install/debug applications and for other purposes of course. However, you can also perform all these by connecting your device via a common Wi-Fi network.

The following steps will enable you to connect your device to your computer via a Wi-Fi network and use the ADB tool. Here’s how to use ADB over Wi-Fi:

  * **Step 1**  
    Connect your Android device to your computer and have USB debugging enabled. Open the terminal/cmd and type:</p> 
    <pre>adb tcpip 5555</pre>
    
    You will get the following message as output:
    
    <pre>restarting in TCP mode port: 5555</pre>
    
    You have successfully enabled ADB over TCP/IP using the port 5555. In case that port is not available, you can use a different one.</li> 
    
      * **Step 2**  
        Get the IP address of your Android device by going to Settings -> About -> Status – IP Address. Type it into the terminal:</p> 
        <pre>adb connect #.#.#.#</pre>
        
        You will get the following message as output:
        
        <pre>connected to #.#.#.#:5555</pre>
    
      * **Step 3**  
        ADB is now connected over Wi-Fi. You can remove the USB cable. Run the following command to confirm if the device is connected or not:</p> 
        <pre>adb devices</pre>
        
        You should get the output as:
        
        <pre>List of devices attached:
#.#.#.#:5555    device</pre></ul> 
    
    P.S. If you want switch back to USB mode, type:
    
        adb usb