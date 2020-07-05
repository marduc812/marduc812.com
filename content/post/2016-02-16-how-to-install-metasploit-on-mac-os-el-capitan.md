---
title: How to install Metasploit on Mac OS El Capitan
author: ヤング marduc
type: post
date: 2016-02-16T14:01:15+00:00
url: /2016/02/16/how-to-install-metasploit-on-mac-os-el-capitan/
featured_image: /wp-content/uploads/2016/02/metasploit.jpg
factory_shortcodes_assets:
  - 'a:0:{}'
dsq_thread_id:
  - 4584185027
mashsb_timestamp:
  - 1587826246
mashsb_jsonshares:
  - '{"total":0,"error":{"facebook_error":"{"error":{"message":"(#12) share field is deprecated for versions v2.9 and higher","type":"OAuthException","code":12,"fbtrace_id":"AkqZJ1qtJQekvPBP6Fet74E"}}"},"facebook_total":0}'
avada_post_views_count:
  - 2282
yuzo_related_post_metabox:
  - 'a:3:{s:17:"yuzo_include_post";s:0:"";s:17:"yuzo_exclude_post";s:0:"";s:21:"yuzo_disabled_related";N;}'
categories:
  - Security
  - Tuts
tags:
  - hack
  - tutorial

---
There were a couple tutorials on the web about how to install Metasploit on Mac OS El Capitan. The orders were to type and type and type commands. The easiest way to do it is by doing a Graphical Installation of Metasploit <!--more-->and with 2 or 3 commands.

### Download Metasploit

Rapid7 offers online a list of the latest builds. What you have to do is to find the one you want. The one I downloaded was **metasploitframework-4.11.10+20160207102256-1rapid7-1.pkg**.

<p style="text-align: center;">
  <a class="button" href="http://osx.metasploit.com/" target="_blank">download link</a>
</p>

### Install Metasploit

This is simple graphical installation for Mac OS. You just follow the steps like you do with every app. You can change the directory of the installation if you want, and the final size of Metasploit is around 300MB. When the installation is complete you can close the Window.

### Launch Metasploit

Launch Terminal from the Applications list and write the following

    /opt/metasploit-framework/bin/msfconsole
    

This will launch Metasploit and you are ready to go!

#### Extra details

If you want to launch Metasploit faster you can use the Alias command on every unix device. So launch your terminal and type the following.

    alias msfconsole='/opt/metasploit-framework/bin/msfconsole'
    

Now anytime you want to launch Metasploit, you just have to type msfconsole and not the whole string. That makes it really faster and easier to launch.