---
title: Hack any device with your Android phone
author: ヤング marduc
type: post
date: 2016-02-06T15:03:35+00:00
url: /2016/02/06/hack-any-device-connected-to-the-same-wifi-with-your-android-phone/
featured_image: /wp-content/uploads/2016/02/Screen-Shot-2016-02-06-at-16.59.27.png
background_selector_orientation:
  - full_width_layout
body_color_rgba:
  - 1
body_source:
  - no-image
body_parallax:
  - 'false'
page_color_rgba:
  - 1
page_source:
  - no-image
page_parallax:
  - 'false'
header_color_rgba:
  - 1
header_source:
  - no-image
header_parallax:
  - 'false'
banner_color_rgba:
  - 1
banner_source:
  - no-image
banner_parallax:
  - 'false'
footer_color_rgba:
  - 1
footer_source:
  - no-image
footer_parallax:
  - 'false'
enable_noti_bar:
  - -1
dsq_thread_id:
  - 4556970299
slide_template:
  - default
factory_shortcodes_assets:
  - 'a:0:{}'
mashsb_timestamp:
  - 1587958660
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"AkOQv0hH99WAqXc3PQuf0zw"}}"},"facebook_total":0}'
avada_post_views_count:
  - 2823
categories:
  - Security
  - Tuts
tags:
  - hack
  - tutorial

---
There are a lot of apps for Android that can help you hack a user. I prefer cSploit. Why? Because it <!--more-->has great layout, it&#8217;s easy to use and it&#8217;s open source.

First of all you need an Android device running Android 2.3 or greater and must be Rooted. Also you need to have installed BusyBox, with every utility. Download BusyBox for free and click the Install button.

<img class="wp-image-516 alignleft" src="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-151326.png" alt="Screenshot_20160206-151326" width="196" height="348" srcset="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-151326.png 405w, http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-151326-768x1365.png 768w" sizes="(max-width: 196px) 100vw, 196px" /> 

Then download cSploit from their github page. The latest version at the moment is 1.6.5. You need to allow the installation of unknown sources. Now open the downloaded .apk in order to install the app.

SuperSU will ask you to allow cSploit to get root permissions. You need to GRAND it and the update the core, the MSF and probably the ruby is the app prompts you to. It will take around 10 minuted depending on your internet speed.

Now you are ready to use the app.

The first thing you see when you launch the app is a list of connected devices on the network. Select your device and select what you want to do.

* * *

## **Image Replacement**

Since we don&#8217;t want do any damage I will use my favourite type of attacks. The Man In The Middle. What happens is the device is now between the Router and my laptop (that I chose as a target) and is manipulating the traffic. So I want to replace every image on the website with one I want. I will replace every image with an image of a cat.

<table style="width: 100%;">
  <tr>
    <td>
      <a href="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153244.png" rel="attachment wp-att-519"><img class="wp-image-519 alignright" src="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153244.png" alt="Screenshot_20160206-153244" width="238" height="423" srcset="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153244.png 405w, http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153244-768x1365.png 768w" sizes="(max-width: 238px) 100vw, 238px" /></a>
    </td>
    
    <td>
      <a href="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153249.png" rel="attachment wp-att-520"><img class="wp-image-520 alignleft" src="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153249.png" alt="Screenshot_20160206-153249" width="238" height="423" srcset="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153249.png 405w, http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-153249-768x1365.png 768w" sizes="(max-width: 238px) 100vw, 238px" /></a>
    </td>
  </tr>
</table>

I prefer picking as a source an image from a website, that the size is about medium.

Here is a preview of the website before and after the attack.

<a href="http://localhost/wp-content/uploads/2016/02/before_after.jpg" rel="attachment wp-att-526"><img class="alignnone size-full wp-image-526" src="http://localhost/wp-content/uploads/2016/02/before_after.jpg" alt="before_after" width="1848" height="1920" srcset="http://localhost/wp-content/uploads/2016/02/before_after.jpg 1848w, http://localhost/wp-content/uploads/2016/02/before_after-768x797.jpg 768w" sizes="(max-width: 1848px) 100vw, 1848px" /></a>

This kind of attack doesn&#8217;t work on https:// that means that it won&#8217;t replace images from websites with SSL.

* * *

## **Password Sniffing**

<a href="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155537.png" rel="attachment wp-att-523"><img class="wp-image-523 aligncenter" src="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155537.png" alt="Screenshot_20160206-155537" width="205" height="365" srcset="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155537.png 1080w, http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155537-768x1365.png 768w" sizes="(max-width: 205px) 100vw, 205px" /></a>  
Also you can do a simple password sniffing for websites that don&#8217;t use https://. For example when I log in to a website it will start to sniff every fields that look like passwords or usernames and this is what it looks like.

The form is **Username : Password INFO: website**

* * *

## **Session Hijacking**

Now a better thing to do is a session highjacking. I will use this attack for an old mail I have. I get connected to the mail&#8217;s website from my laptop, and the app steals the cookies from it. Now there is an option to connect to the website (Left Image). As you can see now I am connected to the website with my username without even getting logged in to it (Right Image). There are really a lot of things to do, but remember to keep it safe for the rest.

<table style="width: 100%;">
  <tr>
    <td>
      <a href="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155842.png" rel="attachment wp-att-525"><img class="wp-image-525 alignright" src="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155842.png" alt="Screenshot_20160206-155842" width="240" height="427" srcset="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155842.png 405w, http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155842-768x1365.png 768w" sizes="(max-width: 240px) 100vw, 240px" /></a>
    </td>
    
    <td>
      <a href="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155837.png" rel="attachment wp-att-524"><img class="wp-image-524 alignleft" src="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155837.png" alt="Screenshot_20160206-155837" width="240" height="426" srcset="http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155837.png 405w, http://localhost/wp-content/uploads/2016/02/Screenshot_20160206-155837-768x1365.png 768w" sizes="(max-width: 240px) 100vw, 240px" /></a>
    </td>
  </tr>
</table>

* * *

### Links

BusyBox:<a href="https://play.google.com/store/apps/details?id=stericson.busybox&hl=en" target="_blank">Google Play</a>  
cSploit: <a href="https://github.com/cSploit/android" target="_blank">GitHub</a> / <a href="https://github.com/cSploit/android/releases/tag/v1.6.5" target="_blank">Download</a>  
SuperSU: <a href="https://play.google.com/store/apps/details?id=eu.chainfire.supersu&hl=en" target="_blank">Google Play</a>

&nbsp;