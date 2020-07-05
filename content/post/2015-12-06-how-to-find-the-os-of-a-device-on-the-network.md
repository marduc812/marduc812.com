---
title: How to find the OS of a device on the network
author: ヤング marduc
type: post
date: 2015-12-06T17:51:34+00:00
url: /2015/12/06/how-to-find-the-os-of-a-device-on-the-network/
featured_image: /wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-networktop.jpg
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
  - 4380951360
mashsb_timestamp:
  - 1587912085
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"AnCqMWJNGJDiS4SD5r2cuk7"}}"},"facebook_total":0}'
avada_post_views_count:
  - 456
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";s:1:"0";}'
categories:
  - Security
  - Tuts
tags:
  - hack
  - tutorial

---
Most of you know about about Metasploit, and how powerful this tool can be.I&#8217;m running Kali Linux 2.0, installed on a virtual machine.<!--more-->

<span style="font-size: x-large;"><strong>1. Start the postgresql service. </strong></span>  
That way we will be able to store the data form the nmap to our database. Postgresql is a DB that is used by Metasploit.

<pre class="brush: bash; title: ; notranslate" title="">service postgresql start
</pre>

This command gets no output so we need to check if postgresql is actually running.  
type:

<pre class="brush: bash; title: ; notranslate" title="">service postgresql status
</pre>

[<img class="alignnone wp-image-476" src="http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network1.png" alt="How to find the OS of a device on the network(1)" width="548" height="72" />][1]

&nbsp;

<span style="font-size: x-large;"><strong>2. Start Metasploit</strong></span>

<pre class="brush: bash; title: ; notranslate" title="">msfconsole
</pre>

Now Metasploit is running. You can use the &#8211;help command if you need more infos about the commands of the platform. There are REALLY a lot of things you can do.

&nbsp;

<span style="font-size: x-large;"><strong>3. NMAP scan the network</strong></span>

<pre class="brush: bash; title: ; notranslate" title="">db_nmap -A 192.168.1.0/24 -v
</pre>

This could take a while depending on how many devices are connected to your network, WiFi&#8217;s signals and more. What each part of the command does:  
**db_nmap** We use it in order to store the data of the nmap to our db.  
**-A** Detects the OS of the devices based on some ports or protocols running.  
**192.168.1.0/24** This is a scan on a range of ips from 192.168.1.0 up to 192.168.1.255.  
**-v** Controls the verbosity of the output. If you want even more details your can use -vv

Now we want to see the list of the connected devices.

<pre class="brush: bash; title: ; notranslate" title="">hosts
</pre>

and what we get is something like that.

[<img class="alignnone  wp-image-490" src="http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network7.jpg" alt="How to find the OS of a device on the network(7)" width="531" height="90" />][2]

<span style="font-size: x-large;"><strong>4. Setting up scan options.</strong></span>

Now we have to use smb_version in order to find more options about the OS. Type the following.

<pre class="brush: plain; title: ; notranslate" title="">use auxiliary/scanner/smb/smb_version
</pre>

By typing **show options** we can see what fields we have to fill.

[<img class="alignnone wp-image-481" src="http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network5.png" alt="How to find the OS of a device on the network(5)" width="509" height="91" />][3]

Now we have to fill the RHOSTS field. This is where we enter the IP of the device we want to find the OS. In my case is 192.168.1.73. To do that we just use the set command.

<pre class="brush: bash; title: ; notranslate" title="">set RHOSTS 192.168.1.73
</pre>

Now we will increase the threads by changing the THREADS number from 1 to 11.

<pre class="brush: bash; title: ; notranslate" title="">set THREADS 11
</pre>

<img class="alignnone wp-image-479" src="http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network4.png" alt="How to find the OS of a device on the network(4)" width="503" height="90" /> 

&nbsp;

<span style="font-size: x-large;"><strong>5. Find the OS</strong></span>

Finally type run and hit enter in order to run the module.

<pre class="brush: bash; title: ; notranslate" title="">run
</pre>

<pre><a href="http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network6.png"><img class="alignnone wp-image-482" src="http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network6.png" alt="How to find the OS of a device on the network(6)" width="522" height="46" />
</a></pre>

And what we can do now is a final hosts and these are our results.

<img class="alignnone wp-image-480" src="http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network3.png" alt="How to find the OS of a device on the network(3)" width="549" height="90" /> 

Now we can see what exactly OS our victim is running and by searching on <a href="https://www.exploit-db.com/" target="_blank">exploits-db</a> we can find the right type of vulnerability that matches our case.

 [1]: http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network1.png
 [2]: http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network7.jpg
 [3]: http://localhost/wp-content/uploads/2015/12/How-to-find-the-OS-of-a-device-on-the-network5.png