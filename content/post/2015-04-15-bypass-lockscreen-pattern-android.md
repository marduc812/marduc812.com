---
title: 'Bypass lockscreen pattern [Android]'
author: ヤング marduc
type: post
date: 2015-04-15T18:41:48+00:00
url: /2015/04/15/bypass-lockscreen-pattern-android/
featured_image: /wp-content/uploads/2015/04/pattern.jpg
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
  - 3686956179
factory_shortcodes_assets:
  - 'a:0:{}'
mashsb_timestamp:
  - 1580303971
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"AR3bh2E7ifGo9JUe5q28ONZ"}}"},"facebook_total":0}'
avada_post_views_count:
  - 704
categories:
  - Android
  - CyanogenMod
  - Tuts
tags:
  - Android
  - CyanogenMod
  - tutorial

---
After updating the latest <a href="http://localhost/category/cyanogenmod/" target="_blank">CM12</a> nightly, my phone asked for unlock pattern. I normally have a 3&#215;3 pattern, but after restart there was just a blank space. All I could feel was a small vibration every time I moved my finger over it. It was a <!--more-->6&#215;6 pattern, set to be invisible. I was trying to unlock the phone but of course there was no way I could do that.

In order to remove password pattern lock phone must be rooted.

Here is what I did.

### 1. Download Android SDK

Since I already had it I didn&#8217;t had to to download it but you can download it, and unzip it somewhere easy to locate.  
<a href="https://developer.android.com/sdk/installing/index.html" target="_blank">Download link</a>

* * *

### 2. Connect THE phone.

I connected my phone with my laptop and open terminal.

* * *

### 3. Open Terminal

Using terminal I had to go to my SDK folder.

First I had to do  
Since I use a Mac in front of adb command I had to use &#8220;/.&#8221;, on linux you don&#8217;t have to.

<pre class="brush: bash; title: ; notranslate" title="">./adb reboot recovery
</pre>

This reboots phone and get&#8217;s it into recovery mode. You can also do it by pressing Power and Volume down button at the same time when you turn on your phone.

<pre class="brush: bash; title: ; notranslate" title="">./adb shell
</pre>

Now we have to run the following commands in order to remove the password/pattern files form the device.

<pre class="brush: bash; title: ; notranslate" title="">rm /data/system/locksettings.db
rm /data/system/locksettings.db-wal
rm /data/system/locksettings.db-shm
rm /data/system/gesture.key
rm /data/system/cm_gesture.key
rm /data/system/password.key
</pre>

Now you have to restart the phone and it won&#8217;t ask you for pattern or password.